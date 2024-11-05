#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
};
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}
void push(struct Node** head_ref, int new_data) {
    struct Node* newNode = createNode(new_data);
    newNode->next = *head_ref;
    *head_ref = newNode;
}
struct Node* findMiddle(struct Node* head) {
    struct Node* slow_ptr = head;
    struct Node* fast_ptr = head;

    if (head != NULL) {
        while (fast_ptr != NULL && fast_ptr->next != NULL) {
            fast_ptr = fast_ptr->next->next;
            slow_ptr = slow_ptr->next;
        }
    }
    return slow_ptr;
}
void insertInMiddle(struct Node** head_ref, int new_data) {
    struct Node* middle_node = findMiddle(*head_ref);

    if (middle_node == NULL) {
        push(head_ref, new_data);
    } else {
        struct Node* newNode = createNode(new_data);
        newNode->next = middle_node->next;
        middle_node->next = newNode;
    }
}
void deleteMiddle(struct Node** head_ref) {
    if (*head_ref == NULL) {
        return;
    }

    if ((*head_ref)->next == NULL) {
        free(*head_ref);
        *head_ref = NULL;
        return;
    }

    struct Node* slow_ptr = *head_ref;
    struct Node* fast_ptr = *head_ref;
    struct Node* prev = NULL;

    while (fast_ptr != NULL && fast_ptr->next != NULL) {
        fast_ptr = fast_ptr->next->next;
        prev = slow_ptr;
        slow_ptr = slow_ptr->next;
    }

    if (prev != NULL) {
        prev->next = slow_ptr->next;
        free(slow_ptr);
    }
}
void printList(struct Node* node) {
    while (node != NULL) {
        printf("%d -> ", node->data);
        node = node->next;
    }
    printf("NULL\n");
}
int main() {
    struct Node* head = NULL;

    push(&head, 5);
    push(&head, 4);
    push(&head, 3);
    push(&head, 2);
    push(&head, 1);

    printf("Original Linked List:\n");
    printList(head);

    insertInMiddle(&head, 10);
    printf("\nAfter Inserting 10 in the middle:\n");
    printList(head);

    deleteMiddle(&head);
    printf("\nAfter Deleting the middle node:\n");
    printList(head);

    return 0;
}
