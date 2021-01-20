leetcode002
---
```
package main

import "fmt"

func main() {
	numbers := addTwoNumbers(head, head1)
}

func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	var carry = 0
	var head =  ListNode{-1, nil}
	var res = &head
	for l1 != nil && l2 != nil {
		temp := l1.Val + l2.Val + carry
		if temp > 9 {
			if res.Val == -1{
				res.Val = temp - 10
			} else {
				res.Next = &ListNode{temp - 10, nil}
				res = res.Next
			}
			if carry==0{
				carry++

			}
		} else {
			if res.Val == -1 {
				res.Val = temp
			} else {
				res.Next = &ListNode{temp, nil}
				res = res.Next
				if carry > 0 {
					carry--
				}
			}

		}

		//fmt.Printf("\n %v %v %v %v", l1.Val, l2.Val, res.Val, temp)
		if res.Next != nil {
			//fmt.Printf("\n next %v", res.Next.Val)

		}

		l1 = l1.Next
		l2 = l2.Next

	}

	for l1 != nil {
		temp := l1.Val + carry
		//fmt.Printf("\n carry %v",carry)
		if temp > 9 {
			res.Next = &ListNode{temp - 10, nil}
			res = res.Next
		} else {
			res.Next = &ListNode{temp, nil}
			res = res.Next
			if carry>0 {
				carry--

			}
		}
		l1 = l1.Next
	}

	for l2 != nil {
		temp := l2.Val + carry
		if temp > 9 {
			res.Next = &ListNode{temp - 10, nil}
			res = res.Next
		} else {
			res.Next = &ListNode{temp, nil}
			res = res.Next
			if carry>0 {
				carry--

			}
		}
		l2 = l2.Next
	}

	for carry > 0 {
		res.Next = &ListNode{1, nil}
		res = res.Next
		carry--
	}

	return &head
}

```
