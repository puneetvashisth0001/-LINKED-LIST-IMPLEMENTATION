# -LINKED-LIST-IMPLEMENTATION

*COMPANY* : CODTECH IT SOLUTIONS

*NAME* : PUNEET VASHISTH

*INTERN ID* : CT04DG757

*DOMAIN* : C PROGRAMMING

*MENTOR* : NEELA SANTOSH

*I USE VS CODE*

THE CIDE IS :

#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

// Function prototypes
void insertAtBeginning(struct Node** head, int data);
void insertAtEnd(struct Node** head, int data);
void deleteByValue(struct Node** head, int key);
void traverse(struct Node* head);

// Insert at the beginning
void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = *head;
    *head = newNode;
    printf("%d inserted at the beginning.\n", data);
}

// Insert at the end
void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = NULL;

    if (*head == NULL) {
        *head = newNode;
        printf("%d inserted as the first node.\n", data);
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    printf("%d inserted at the end.\n", data);
}

// Delete node by value
void deleteByValue(struct Node** head, int key) {
    struct Node *temp = *head, *prev = NULL;

    // If head node itself holds the key
    if (temp != NULL && temp->data == key) {
        *head = temp->next;
        free(temp);
        printf("Node with value %d deleted.\n", key);
        return;
    }

    // Search for the key
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    // Key not found
    if (temp == NULL) {
        printf("Value %d not found in the list.\n", key);
        return;
    }

    // Unlink and free
    prev->next = temp->next;
    free(temp);
    printf("Node with value %d deleted.\n", key);
}

// Traverse and display the list
void traverse(struct Node* head) {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }

    printf("Linked List: ");
    while (head != NULL) {
        printf("%d -> ", head->data);
        head = head->next;
    }
    printf("NULL\n");
}

// Main function with a simple menu
int main() {
    struct Node* head = NULL;
    int choice, value;

    do {
        printf("\nMenu:\n");
        printf("1. Insert at beginning\n");
        printf("2. Insert at end\n");
        printf("3. Delete by value\n");
        printf("4. Traverse\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            printf("Enter value to insert: ");
            scanf("%d", &value);
            insertAtBeginning(&head, value);
            break;
        case 2:
            printf("Enter value to insert: ");
            scanf("%d", &value);
            insertAtEnd(&head, value);
            break;
        case 3:
            printf("Enter value to delete: ");
            scanf("%d", &value);
            deleteByValue(&head, value);
            break;
        case 4:
            traverse(head);
            break;
        case 5:
            printf("Exiting program.\n");
            break;
        default:
            printf("Invalid choice! Try again.\n");
        }
    } while (choice != 5);

    return 0;
}

* VS CODE OUTPUT IS *
* <img width="244" height="141" alt="Image" src="https://github.com/user-attachments/assets/383f107d-d5f7-4fa5-8dc3-334ce109bd8c" />
