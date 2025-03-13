# ToDoListclass ToDoList:
 def __init__(self):
 self.tasks = {} # Dictionary to store tasks {task_number: (task, status
 def add_task(self, task):
 task_number = len(self.tasks) + 1
 self.tasks[task_number] = (task, "Pending")
 print(f"Task '{task}' added successfully.")
 def view_tasks(self):
 if not self.tasks:
 print("No tasks available.")
 else:
 print("\nYour To-Do List:")
 for num, (task, status) in self.tasks.items():
 print(f"{num}. {task} - [{status}]")
 def mark_completed(self):
 if not self.tasks:
 print("No tasks available to mark as completed.")
 return
 # Display tasks before asking for input
 self.view_tasks()
 
 try:
 task_number = int(input("Enter task number to mark as completed: "))
 if task_number in self.tasks:
 task, _ = self.tasks[task_number]
 self.tasks[task_number] = (task, "Completed")
 print(f"Task '{task}' marked as completed.")
 else:
 print("Invalid task number.")
 except ValueError:
 print("Invalid input! Please enter a valid task number.")
 def remove_task(self):
 if not self.tasks:
 print("No tasks available to remove.")
 return
 # Display tasks before asking for input
 self.view_tasks()
 try:
 task_number = int(input("Enter task number to remove: "))
 if task_number in self.tasks:
 task = self.tasks.pop(task_number)
 print(f"Task '{task[0]}' removed.")
 # Reorder task numbers after removal
 self.tasks = {i+1: v for i, v in enumerate(self.tasks.values())}
 else:
 print("Invalid task number.")
 except ValueError:
 print("Invalid input! Please enter a valid task number.")
# Main Program
def main():
 todo = ToDoList()
 
 while True:
 print("\nTO-DO LIST MENU")
 print("1. Add Task")
 print("2. View Tasks")
 print("3. Mark Task as Completed")
 print("4. Remove Task")
 print("5. Exit")
 
 try:
 choice = int(input("Enter your choice: "))
 
 if choice == 1:
 task = input("Enter the task: ")
 todo.add_task(task)
 elif choice == 2:
 todo.view_tasks()
 elif choice == 3:
 todo.mark_completed()
 elif choice == 4:
 todo.remove_task()
 elif choice == 5:
 print("Exiting To-Do List. Have a productive day!")
 break
 else:
 print("Invalid choice! Please enter a number between 1 and 5.")
 except ValueError:
 print("Invalid input! Please enter a number.")
# Run the program
if __name__ == "__main__":
 main()
