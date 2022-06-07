# BM1 反转链表

[NowCoder](https://www.nowcoder.com/practice/75e878df47f24fdc9dc3e400ec6058ca?tpId=295&tqId=23286&ru=/exam/oj&qru=/ta/format-top101/question-ranking&sourceUrl=%2Fexam%2Foj)
## 解题思路


###step 1：优先处理空链表，空链表不需要反转。

###step 2：我们可以设置两个指针，一个当前节点的指针，一个上一个节点的指针（初始为空）。

###step 3：遍历整个链表，每到一个节点，断开当前节点与后面节点的指针，并用临时变量记录后一个节点，然后当前节点指向上一个节点，即可以将指针逆向。

###step 4：再轮换当前指针与上一个指针，让它们进入下一个节点及下一个节点的前序节点。

### 递归

```java
public class Solution {
    public ListNode ReverseList(ListNode head) {
        if(head==null||head.next==null){
            return head;
        }
        ListNode prehead = ReverseList(head.next);
        head.next.next = head;
        head.next = null;
        return prehead;
    }
}
```

### 双指针



```java
public class Solution {
    public ListNode ReverseList(ListNode head) {
       
        ListNode pre=null;
        ListNode p=head;
        while(p!=null){
            ListNode temp=p.next;
            p.next=pre;
            pre=p;
            p=temp;
        }
        return pre;
        
 
    }
}
```
