####回溯

##### 剑指 Offer 34. 二叉树中和为某一值的路径

+ 描述

```
 输入一棵二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径。
 			  5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
        
```

+ 题解

  ```java
  class Solution {
  
      private  List<List<Integer>> res;
  
      public List<List<Integer>> pathSum(TreeNode root, int sum) {
          //回溯
          res = new ArrayList<>();
          backtrack(root , sum , new ArrayList<>());
          return res;
      }
  
      private void backtrack(TreeNode node, int target, List<Integer> list) {
          if (node == null) {
              return;
          }
          list.add(node.val);
          target =  target -node.val;
          if (target == 0 && node.left == null && node.right == null) {
              res.add(new ArrayList<>(list));
          } else {
              backtrack(node.left, target, list);
              backtrack(node.right, target, list);
          }
          list.remove(collector.size() - 1);
      }
  }
  ```

  

  ```java
  class Solution {
      LinkedList<List<Integer>> res = new LinkedList<>();
      LinkedList<Integer> path = new LinkedList<>(); 
  
      public List<List<Integer>> pathSum(TreeNode root, int sum) {
          recur(root, sum);
          return res;
      }
      
      void recur(TreeNode root, int tar) {
          if(root == null) return;
          path.add(root.val);
          tar -= root.val;
          if(tar == 0 && root.left == null && root.right == null)
              res.add(new LinkedList(path));
          recur(root.left, tar);
          recur(root.right, tar);
          path.removeLast();
      }
  }
  ```

  

```java

```

