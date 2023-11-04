# Big_O_Notation
In this exercise, you’ll analyze expressions and code to figure out the time complexity

## Step One: Simplifying Expressions
Here are the simplified forms of the given big O expressions:

O(n + 10) = O(n) (We drop the constant term, as it doesn't affect the order of growth)
O(100 * n) = O(n) (We drop the constant factor)
O(25) = O(1) (Constant time complexity)
O(n^2 + n^3) = O(n^3) (We take the highest order term)
O(n + n + n + n) = O(4n) = O(n) (We combine like terms and drop the constant factor)
O(1000 * log(n) + n) = O(n) (The linear term dominates)
O(1000 * n * log(n) + n) = O(n * log(n)) (The n * log(n) term dominates)
O(2^n + n^2) = O(2^n) (Exponential growth dominates)
O(5 + 3 + 1) = O(1) (Constant time complexity)
O(n + n^(1/2) + n^2 + n * log(n)^10) = O(n^2) (The n^2 term dominates, as it is the highest order term)
Keep in mind that when simplifying big O expressions, we focus on the dominant term that contributes the most to the growth of the function as the input size n becomes large.

## Step Two: Calculating Time Complexity
Determine the time complexities for each of the following functions. If you’re not sure what these functions do, copy and paste them into the console and experiment with different inputs!

function logUpTo(n) {
  for (let i = 1; i <= n; i++) {
    console.log(i);
  }
}
​
### This function logs numbers from 1 to n, so it has a linear time complexity because it runs a loop that goes from 1 to n.
### Time Complexity: O(n)

function logAtLeast10(n) {
  for (let i = 1; i <= Math.max(n, 10); i++) {
    console.log(i);
  }
}
​
### This function logs numbers from 1 to the maximum of n and 10, so it also has a linear time complexity, similar to logUpTo(n). The loop runs either n times or 10 times, whichever is larger.
### Time Complexity: O(max(n, 10))



function logAtMost10(n) {
  for (let i = 1; i <= Math.min(n, 10); i++) {
    console.log(i);
  }
}
​
### This function logs numbers from 1 to the minimum of n and 10. The loop runs either n times or 10 times, whichever is smaller.
### Time Complexity: O(min(n, 10))

function onlyElementsAtEvenIndex(array) {
  let newArray = [];
  for (let i = 0; i < array.length; i++) {
    if (i % 2 === 0) {
      newArray.push(array[i]);
    }
  }
  return newArray;
}
​
### This function iterates over an array and only selects elements at even indices, which is essentially half the length of the array. Therefore, the time complexity is linear in terms of the array length.
### Time Complexity: O(n/2) => O(n)

function subtotals(array) {
  let subtotalArray = [];
  for (let i = 0; i < array.length; i++) {
    let subtotal = 0;
    for (let j = 0; j <= i; j++) {
      subtotal += array[j];
    }
    subtotalArray.push(subtotal);
  }
  return subtotalArray;
}
​
### This function calculates subtotals for each element in the input array. It uses nested loops, and the inner loop depends on the outer loop. This function has a quadratic time complexity because the number of operations is proportional to the square of the input size.
### Time Complexity: O(n^2)

function vowelCount(str) {
  let vowelCount = {};
  const vowels = "aeiouAEIOU";

  for (let char of str) {
    if(vowels.includes(char)) {
      if(char in vowelCount) {
        vowelCount[char] += 1;
      } else {
        vowelCount[char] = 1;
      }
    }
  }

  return vowelCount;
}
​
### This function counts the occurrences of vowels in a string. It iterates over each character in the string and performs constant-time operations for each character. The time complexity is linear in terms of the length of the input string.
### Time Complexity: O(n), where n is the length of the input string.

Keep in mind that the actual time complexity might vary slightly based on the specific implementation and language optimizations, but these are good approximations for understanding the growth of these functions with respect to their inputs.

## Part 3 - short answer
Answer the following questions

1. True or false: n^2 + n is O(n^2).
Answer: True. n^2 + n is indeed O(n^2) because we focus on the highest-order term, which is n^2.

2. True or false: n^2 * n is O(n^3).
Answer: True. n^2 * n is O(n^3) because it's the same as n^3 when considering big O notation.

3. True or false: n^2 + n is O(n).
Answer: False. n^2 + n is not O(n) because n^2 dominates the growth, so it's O(n^2).

3. What’s the time complexity of the .indexOf array method?
Answer: The time complexity of the .indexOf array method is O(n) in the worst case. It needs to potentially search through the entire array to find the target element.

4. What’s the time complexity of the .includes array method?
Answer: The time complexity of the .includes array method is O(n) in the worst case, similar to .indexOf. It may have to check each element to determine if the array includes the target value.

5. What’s the time complexity of the .forEach array method?
Answer: The time complexity of the .forEach array method is O(n). It iterates over each element in the array exactly once.

6. What’s the time complexity of the .sort array method?
Answer: The time complexity of the .sort array method depends on the implementation, but the standard JavaScript Array.prototype.sort() uses a variant of the merge sort algorithm, which has an average and worst-case time complexity of O(n log n).

7. What’s the time complexity of the .unshift array method?
Answer: The time complexity of the .unshift array method is O(n) because it has to shift all existing elements to make space for the new element at the beginning of the array.

8. What’s the time complexity of the .push array method?
Answer: The time complexity of the .push array method is O(1) on average. It appends an element to the end of the array in constant time. However, in some cases, when the array needs to be resized, it may be O(n), but this is amortized over multiple operations.

9. What’s the time complexity of the .splice array method?
Answer: The time complexity of the .splice array method is O(n). It can remove and insert elements in the middle of an array, which may require shifting elements to maintain the order.

10. What’s the time complexity of the .pop array method?
Answer: The time complexity of the .pop array method is O(1) because it removes the last element from an array in constant time.

11. What’s the time complexity of the Object.keys() function?
Answer: The time complexity of the Object.keys() function is O(n), where 'n' is the number of keys in the object. It iterates through all the enumerable properties of the object to retrieve their keys.

BONUS

13. What’s the space complexity of the Object.keys() function?
Answer: The space complexity of the Object.keys() function is O(n), where 'n' is the number of keys in the object. It needs to create an array to store the keys, and the size of that array is directly proportional to the number of keys in the object.
