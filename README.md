#include <stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node *next;
};
// #include<stdlib.h>
void display_list(struct node *head){
    struct node *cur=head;
    while(cur!=NULL){
        printf("%d ",cur->data);
        cur=cur->next;
    }
    printf("\n");
}
struct node *make_node(int val){
    struct node *nd;
    nd=(struct node*)malloc(sizeof(struct node));
    nd->data=val;
    nd->next=NULL;
    return nd;
}
struct node *insert_front(int val,struct node *head){
    struct node *newnode;
    newnode=make_node(val);
    newnode->next=head;
    head=newnode;
    return head;
    
}
void insert_end(int val,struct node **head){
    struct node *newnode=make_node(val);
    struct node *tempnode=*head;
    if(*head==NULL){
        *head=newnode;
        // return 
    }
    else{
        while (tempnode->next!=NULL){
            tempnode=tempnode->next;
        }
        tempnode->next=newnode;
    }
    
    
}
int main() {
	struct node *head=NULL;
	int x;
	scanf("%d\n",&x);
	while (x--){
	    int val;
	    scanf("%d",&val);
	   head=insert_front(val,head);
	}
	display_list(head);
	return 0;
}
