# COD-TECH-TASK2
class StudentGrades:
    def __init__(self, student_name):
        self.student_name = student_name
        self.grades = {}

    def add_grade(self, subject, grade):
        if 0 <= grade <= 100:
            self.grades[subject] = grade
        else:
            print("Grade should be between 0 and 100.")

    def calculate_average(self):
        if not self.grades:
            return 0
        return sum(self.grades.values()) / len(self.grades)

    def calculate_letter_grade(self, avg):
        if avg >= 90:
            return 'A'
        elif avg >= 80:
            return 'B'
        elif avg >= 70:
            return 'C'
        elif avg >= 60:
            return 'D'
        else:
            return 'F'

    def calculate_gpa(self, avg):
        if avg >= 90:
            return 4.0
        elif avg >= 80:
            return 3.0
        elif avg >= 70:
            return 2.0
        elif avg >= 60:
            return 1.0
        else:
            return 0.0

    def display_student_info(self):
        avg = self.calculate_average()
        letter_grade = self.calculate_letter_grade(avg)
        gpa = self.calculate_gpa(avg)

        print(f"Student: {self.student_name}")
        print("Grades:", self.grades)
        print(f"Average Grade: {avg:.2f}")
        print(f"Letter Grade: {letter_grade}")
        print(f"GPA: {gpa:.2f}")

def main():
    student = StudentGrades(input("Enter student name: "))
    
    while True:
        subject = input("Enter subject (or 'done' to finish): ")
        if subject.lower() == 'done':
            break
        try:
            grade = float(input(f"Enter grade for {subject}: "))
            student.add_grade(subject, grade)
        except ValueError:
            print("Please enter a valid number for the grade.")

    student.display_student_info()

if __name__ == "__main__":
    main()
