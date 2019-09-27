# Array-Unique-Element-Count-Extension
A detailed explanation of how the array unique element count extension using a tuple works



## Step 1 - Creating the extension
- This block of code shows the syntax of an Array extension
- This particular extension has the type *Comparable* which means items can be compared using relational operators such as <, <=, >, =>

       swift extension Array where Element: Comparable {}
   
## Step 2 - Creating a function
- This function should be used to count the number of unique elements within an array
- This function should return an Integer

        func countUniqueElements() -> Int {}
        
- The next line of code will declares a variable named sort which is to be sorted in ascending order
- Notice *Comparable* allows for the use of <

         let sorted = self.sorted(by: <)
   
- The following line is where the tuple is created 
- The tuple will store two elements. The first is the element (Element!) that was inspected last, while the second item (Int) is the current count of unique elements
- Since Element! was specified .none can be used for the value, and because there is currently no count the value is 0

        let start: (Element?, Int) = (.none, 0)
        
- This is the chunk of the code where the items within the array will be sorted
- It will iterate through the array pulling out one item at a time. If the element is of a different value than the previous it moves on to a different item. This will continue until all the elements in the array are sorted in the correct order and the current element and the unique count are returned.

        let result = sorted.reduce(start) {
            (previousResult, currentElement) in
            var uniqueCount = previousResult.1
            if (previousResult.0 != currentElement) {
                uniqueCount += 1
            }
            return((currentElement, uniqueCount))
        }

- the function ends and the result is returned

        return result.1
        
 ## Step 3 - Testing
 
 - Start by defining an array
 
        let values = [-1, -4, 0, 4, 34, 5, 0, -1, -1, -4, 0, 5]
        
 - Call the function
 
        let uniqueValuesCount = values.countUniqueElements()
        
 - Print the result, which in this case it should print 6
 
        print(uniqueValuesCount)
        
        
 #### To view the code in its entirety click here
 https://github.com/oliviabishop/Array-Unique-Element-Count-Extension/wiki/Array-Unique-Element-Count-Project
