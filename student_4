// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract StudentRecords {
    struct Student { uint256 id; string name; uint8 age; }
    Student[] private students;
    mapping(uint256 => bool) private idExists;

    event StudentAdded(uint256 indexed id, string name);

    function addStudent(uint256 id, string calldata name, uint8 age) external {
        require(id > 0 && !idExists[id], "Invalid or duplicate ID");
        require(bytes(name).length > 0, "Name required");
        students.push(Student(id, name, age));
        idExists[id] = true;
        emit StudentAdded(id, name);
    }

    function getStudent(uint256 index) external view returns (uint256, string memory, uint8) {
        require(index < students.length, "Index out of range");
        Student memory s = students[index];
        return (s.id, s.name, s.age);
    }

    function getStudentCount() external view returns (uint256) { return students.length; }

    // Fallback handles unknown non-empty function calls.
    fallback() external payable { }
    receive() external payable { }
}
