<h1> Algorithm for File Updates In Python</h1>


<h3>Project Description</h3>
In this project I am creating an algorithm to automatically update the  allowed IP addresses to restricted content. The “allow_list.txt” are the IP addresses that have permission to access this content. There is a second list that identifies IP addresses that should no longer have access to this content. The algorithm I created will automate updating the “allow_list.txt” file and remove IP addresses that should no longer be able to access the content.
<br />
<br />

<h4>Open the file that contains the allow_list<h4></h4><br />  
<p align="center">
I start out the algorithm by first opening the “allow_list.txt” file. I assigned this file name as a string to the “import_file” variable: <br/>
<br />
<img src="https://i.imgur.com/VELgu0s.png"  height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then, using the with statement I opened the file <br/>
<br />
<img src="https://i.imgur.com/ycPssXz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In this algorithm, the with statement is used with the .open() function in read mode to open the allow list file for the purpose of reading it. I need to open the files so I can  access the IP addresses stored in the allow list file. The with keyword will help manage the resources by closing the file after exiting the with statement. In the code with open(import_file, "r") as file:, the open() function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, "r" indicates that I want to read it. The code also uses the as keyword to assign a variable named file; file stores the output of the .open() function while I work within the with statement.<br />
<br />
<br />
<h4>Read the file contents</h4><br />
<p align="center">
Next I will use the .read() method to convert it into the string. <br/>
<br/>
<img src="https://i.imgur.com/7Cy8Gci.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
So when I use the .open() function that includes the argument "r" for “read,” I can call the .read() function in the body of the with statement. The .read() method converts the file into a string and allows me to read it. I applied the .read() method to the file variable identified in the with statement. Then, I assigned the string output of this method to the variable ip_addresses. This code then reads the contents of the "allow_list.txt" file into a string format which gives me the ability to later use the string to organize and extract data in my Python program.<br />

<br />
<br />
<h4>Convert the string into a list</h4><br />
<p align="center">
<br />
Now I need to convert the string into a list so I can remove the IP addresses that should no longer have access to this content. To accomplish this I needed to utilize the .split() method to convert ip_addresses string into a list:   <br/>
<br/>
<img src="https://i.imgur.com/9sSVeKz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The .split() function is called by appending it to a string variable. It turns the contents of the string into list. I split the  ip_addresses into a list to make it easier to remove IP addresses from the allow list. The .split() function splits the text by whitespace into list elements. In this algorithm, the .split() function takes the data stored in the variable ip_addresses, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable ip_addresses. <br />

<br />
<br />
<h4>Iterate through the remove list </h4><br />
<p align="center">
<br />
The next part of the algorithm involves iterating through the IP addresses that are elements in the remove_list. To do this, I utilized a for loop:  <br/>
<br />
<img src="https://i.imgur.com/Tlp3ZSF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The for loop in Python repeats code for a specified sequence. The overall purpose of the for loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The for keyword starts the for loop. It is followed by the loop variable element and the keyword in. The keyword in indicates to iterate through the sequence ip_addresses and assign each value to the loop variable element.  <br />
<br />
<br />
<h4>Remove IP addresses that are on the remove list </h4><br />
<p align="center">
This algorithm requires me to remove any IP address from the allow list, ip_addresses, that is also contained in remove_list.  Because there were not any duplicates in ip_addresses, I was able to use the following code to do this:  <br/>
<br/>
<img src="https://i.imgur.com/s2AE2u8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In my for loop, I created a conditional that evaluated whether or not the loop variable element was found in the ip_addresses list. The reason I did that was because when I utilize .remove() to elements that were not found in ip_addresses would result in an error. 
<br />
Then, within that conditional, I applied .remove() to ip_addresses. I passed in the loop variable element as the argument so that each IP address that was in the remove_list would be removed from ip_addresses.  <br />
<br />
<br />
<h4>Update the file with the revised list of IP addresses </h4><br />
<p align="center">
<br />
As a final step of the algorithm, I needed to update the allow list file with the revised list of IP addresses. To do this, I needed to convert the list back into a string so I used the .join() method for this:  <br/>
<br />
<img src="https://i.imgur.com/gAq5aZd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The .join() method combines all items in an iterable into a string. The .join() method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. In this algorithm, I used the .join() method to create a string from the list ip_addresses so that I could pass it in as an argument to the .write() method when writing to the file "allow_list.txt". I used the string ("\n") as the separator to instruct Python to place each element on a new line. 
<br />
Then, I used another with statement and the .write() method to update the file:.  <br />
<br />
<br />
<img src="https://i.imgur.com/WjDrJma.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br />
This time, I used a second argument of "w" with the open() function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument "w", I can call the .write() function in the body of the with statement. The .write() function writes string data to a specified file and replaces any existing file content. 
I needed to write the updated allow list as a string to the file "allow_list.txt". This way, any IP addresses removed from the allow list will no longer be allowed to access the restricted content. To rewrite the file, I appended the .write() function to the file object file that I identified in the with statement. I passed in the ip_addresses variable as the argument to specify that the contents of the file specified in the with statement should be replaced with the data in this variable.  <br/>
<br/>
<br />
<h4>Summary </h4><br />
<p align="center">
<br />  
I created an algorithm that removes IP addresses identified in a remove_list variable from the "allow_list.txt" file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable ip_addresses. I then iterated through the IP addresses in remove_list. With each iteration, I evaluated if the element was part of the ip_addresses list. If it was, I applied the .remove() method to it to remove the element from ip_addresses.. After this, I used the .join() method to convert the ip_addresses back into a string so that I could write over the contents of the "allow_list.txt" file with the revised list of IP addresses.  <br/>

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
