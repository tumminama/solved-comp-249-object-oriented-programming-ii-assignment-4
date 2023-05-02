Download Link: https://assignmentchef.com/product/solved-comp-249-object-oriented-programming-ii-assignment-4
<br>
<strong>Purpose:</strong>  The purpose of this assignment is to allow you practice Object Oriented Design, File I/O, Exception Handling, Interfaces, ArrayList, and Linked Lists.




The objective of this programming assignment is to create a fully functioning system that handles Concordia University payment system. The system will be used by the university to calculate the payment of the different <em>employees </em>(e.g. full time and part time instructors, teaching assistants and staff); and also the payment of different <em>services</em> such as  electricity, phone, snow removal, cleaning, etc.

Based on the following narrative, you need to come up with an Object-Oriented design to represent the different entities in the system. Like in real world, some of the narratives are just noise and has nothing to do with the payment system. It is your task to filter out the noise.

It is expected that your implementation handles the appropriate exceptions if the user tries to enter information of the wrong (unexpected) type. That is, you need to take into account any possible incorrect entries by the user. Additionally, you should take advantage of code reuse through inheritance and polymorphism whenever needed.




You should notice that all information provided in this assignment (names, salary, rules of payment, and all other specifics) are merely fictitious and have no real merits whatsoever in reality. This information is only provided to allow simulation of the system. Additionally, when you add further records, please avoid using any real names!




The assignment has <strong>two parts</strong>. <strong>Part 1 is mandatory</strong>, whereas <strong>Part 2 is optional</strong>; however <u>completing it entirely and</u> <u>correctly</u> can earn you <strong>4 bonus points.</strong>




<strong><u>Part 1: Employees (10 pts)</u> </strong>

<strong> </strong>

At Concordia University, we have <em>students</em>, <em>faculty</em>, and <em>staff members</em>. Below are the details for the different categories of employees:




<ul>

 <li>In order for a <em>student </em>to qualify for a teaching assistant (TA) position, the student must be a current registered student; an alumnus cannot be a TA. The TA is paid by a fixed-rate times the number of hours in his/her contract. We have two kinds of TA’s: a graduate teaching assistant (GD_TA) and an undergraduate teaching assistant (UD_TA). The rate is slightly different for each; the GD_TA’s rate is 1.2 the UD_TA’s rate. The current fixed rate for an UD_TA is 18.25$/hr.</li>

</ul>




<ul>

 <li>For <em>faculty</em> members, we have permanent and part-time members. A permanent faculty is paid a fixed salary, whereas, the part-time faculty is paid based on the number of hours in the contract. For part time faculty members, if the class size is between 40 and 60 students, they get an extra $500. If the class size is &gt;60, they get an extra $1000. Each part time member can teach exactly one course per term. The term is 4 month.</li>

</ul>




<ul>

 <li>All university <em>staff</em> members are permanent and have a fixed annual salary, which increases every 3 years by a bonus percentage based on a performance code. The performance code is assigned to the employee by his/her direct supervisor. Here are the different performance codes, and their effects on the bonus calculation:</li>

</ul>

<table width="149">

 <tbody>

  <tr>

   <td width="49">Code</td>

   <td width="48"></td>

   <td width="52">Bonus %</td>

  </tr>

  <tr>

   <td width="49">A</td>

   <td width="48"></td>

   <td width="52">8%</td>

  </tr>

  <tr>

   <td width="49">B</td>

   <td width="48"></td>

   <td width="52">6%</td>

  </tr>

  <tr>

   <td width="49">C</td>

   <td width="48"></td>

   <td width="52">3%</td>

  </tr>

  <tr>

   <td width="49">D</td>

   <td width="48"></td>

   <td width="52"> 1%</td>

  </tr>

  <tr>

   <td width="49">E</td>

   <td width="48"></td>

   <td width="52">0%</td>

  </tr>

 </tbody>

</table>

(<em><u>Note:</u></em> an x% bonus indicated x% increase of the salary)

<ul>

 <li>The initial information of <em>full-time faculty</em> members are maintained in a file called <strong><em>Full-Time-Faculty.txt</em></strong>. Each record</li>

</ul>

in this file is composed of: Employee ID, First Name, Family Name, City of Residence, Hire Year, and Salary.




<ul>

 <li>The initial information of <em>part-time faculty</em> members are maintained in a file called <strong><em>Part-Time-Faculty.txt</em></strong><strong>.</strong> Each record</li>

</ul>

in this file is composed of: Employee ID, First Name, Family Name, City of Residence, Hire Year, Hourly Rate, Number of Hours of Current Term, and Number of Student in

Class.  The Hire Year indicates the first year the professor joined the university.




<ul>

 <li>The initial information of <em>staff</em> members are maintained in a file called <strong><em>txt</em></strong>. Each record in this file is composed</li>

</ul>

of: Employee ID, First Name, Family Name, City of Residence, Hire Year, Salary, and performance code.







Now, while the information in the above three files are correct, the information of the file related to the TAs, <strong><em>TAs.txt</em></strong>, is somehow corrupt and hence it includes extra records that are incorrect. In specific, the file includes records that shows some alumnus as TAs, which is not permitted. These records must be treated correctly by your code, as explained below. The general format of the records of the <strong><em>TAs.txt</em></strong> file is as follows:

Employee ID, First Name, Family Name, City of Residence, Hire Year, Classification of TA (which can be , Grad, UGrd, or Alum), Current Number of Classes the TA is involved with, and Total

Number of Working Hours for these Courses. The Hire Year indicates the first year the TA was first assigned any TA contract at the university.




You are required to design and write the implementation of the employees’ payment subsystem, these are the needed requirements:




<ol>

 <li>Write the code of <strong>3</strong> methods called <strong><em>addFTRecords()</em></strong>, <strong><em>addPTRecords()</em></strong> and <strong><em>addTARecords()</em></strong>. Each of these methods must work exactly as follows:

  <ol>

   <li>Open the proper text file (i.e. for Full-time, Part-time, TA) and reads its contents into an <strong>ArrayList</strong>. This method (and all following methods) may choose to accept an already open stream of the files, or open them inside the method; this is left for you to decide.)</li>

   <li>Prompt the user requiring the information of the new record to be added. The user is expected to enter an employee ID, followed by the rest of the record. The user enters -1 to indicate that he/she has no more records to add. However the user may mistakenly enter an Employee ID that already exists. Your code must detect this problem and reject the entry, then keep looping until the user enters a non-existing ID. You should notice that the entered ID must not match any of the existing IDs in any of the files (Hint: You should take an advantage of the <em>contains()</em> method of ArrayList).</li>

   <li>All these entered new records must be kept in the ArrayList. Once the user enters -1, the ArrayList must be stored in the related text file; consequently the file is permanently updated with the new records.</li>

  </ol></li>

</ol>




<ol start="2">

 <li>Write the code of a method called <strong><em>findTermSalary()</em></strong><em>,</em> which calculates the combined total salary of part-time faculty and teaching assistants (TAs). This method must exactly work as follows:

  <ol>

   <li>Open the proper text files and read them into a <strong>Linked List</strong>. <u>You are required to design</u> this Linked List (i.e. you must write the class and all the methods of this linked list). <u>Do NOT</u> use any data types provided by the Java programming language. Additionally, you should take advantage of inner classes when designing this Linked List class.</li>

   <li>Iterates through the two linked lists and calculate the combined total salary of part-time faculty and TAs</li>

   <li>Display a message with this information (i.e. just use <em>out.println()</em>).</li>

  </ol></li>

</ol>




<ol start="3">

 <li>Write the code of a method called <strong><em>findHighest_and_Lowest_FT_Salary()</em></strong>, which finds the highest and lowest salary for any full-time faculty. This method must exactly work as follows:

  <ol>

   <li>Open the <em>Full-Time-Faculty.txt</em> file and read it into a Linked List, you should use the same linked list class that you already created above.</li>

   <li>Search the list for the highest and lowest salaries, and display the full record of these employees. In case multiple records exist with highest and lowest salaries (i.e. 2 or more employees have the same highest salary; you need to display all of them.)</li>

  </ol></li>

</ol>




<ol start="4">

 <li>Write the code of a method called <strong><em>Increase_Staff_Salary()</em></strong>.This method must exactly work as follows:

  <ol>

   <li>Open the <em>txt</em> file and read it into a Linked List similar to what you did above.</li>

   <li>Iterate into all records and increase the salaries based on the performance evaluation code. For example, if the salary of a staff is 62,000$ and the last evaluation code is B, then the salary must be changed to 65,720$, which reflects the 6% increase.</li>

   <li>You must also reset all salary increase codes afterwards to E, so further calls for this method before the evaluation take place again (in another 3 years) do not result in multiple incorrect increases.</li>

   <li>Save the contents of the linked list into the <em>txt</em> file; hence permanently changing the salaries to reflect the increases, and resetting bonus codes.</li>

  </ol></li>

</ol>




<ol start="5">

 <li>Write an interface called <strong>Ordered</strong>. This interface must have two abstract methods, called <strong><em>precedes()</em></strong> and <strong><em>follows()</em></strong>. Each of these methods expects one parameter, of type Object, and returns a Boolean value. The semantics of these methods are as follows:

  <ol>

   <li><strong><em>precedes()</em></strong> returns <em>true</em> if the calling object precedes the passed object, based on a given rule that will eventually be set by the class implementing the interface; otherwise the method returns <em>false</em>;</li>

   <li><strong><em>follows()</em></strong> returns <em>true</em> if the calling object follows the passed object, based on a given rule that will eventually be set by the class implementing the interface; otherwise the method returns <em>false</em>;</li>

   <li>The Employee class must implements the <strong>Ordered</strong> The semantics of the two methods are as follows:</li>

   <li><strong><em>precedes()</em></strong> returns <em>true</em> if the Hire Year of the calling Employee precedes the Hire Year of the passed Employee (for example 1998 precedes 2017); otherwise the method returns false. ii. <strong><em>follows()</em></strong> returns <em>true</em> if the Hire Year of the calling Employee follows the Hire Year of the passed Employee (for example, 2016 follows 2009); otherwise the method returns false.</li>

  </ol></li>

</ol>




<ol start="6">

 <li>You must submit a UML class diagram that shows your classes, their hierarchy and their relations.</li>

</ol>










<strong><u>Part 2: Services [Bonus 4pts]*</u> </strong>




Concordia does not only pay employees, it has to pay suppliers bills too. There are two types of suppliers’ bills: <em>subscription</em> and <em>service</em> bills.

<ul>

 <li><em>Subscriptions</em> are regular payment bills with a fixed amount of money paid weekly, bi-weekly, monthly, trimester, semester, or yearly for services used by the university from providers such as electricity, phone, internet, e-books, magazines, etc. (take advantage of enumerator to design this information).</li>

 <li><em>Services</em> are payment bills with varying amount of money paid based the hourly rate of the service such as snow removal, cleaning, painting, plumbing, security, etc.</li>

</ul>




The bookkeeping information of the different bills is maintained in a file called <strong><em>Bills.txt</em></strong>. Below are the details for the two suppliers’ bills:




<ul>

 <li><em>Subscription </em>bills: Each subscription supplier has Supplier ID, supplier Name, Company Name, start Year, Bill number, subscription type, Subscription amount.</li>

</ul>




<ul>

 <li><em>Service</em> bills: Each service supplier has Supplier ID, Service Name, Company Name, Start Year, Bill number, Number of hours, hour rate, and Total bill.</li>

</ul>







You are required to design and write the implementation of the bills payment subsystem, you should take advantage of inheritance, polymorphism and interfaces as needed. These are the requirements:







<ol>

 <li>Write the code of <strong>3</strong> methods called <strong><em>addBill()</em></strong>, <strong><em>updateBill()</em></strong> and <strong><em>RemoveBill()</em></strong>. Each of these methods must work exactly as follows:

  <ol>

   <li>Opens the txt file and reads its contents into an <strong>ArrayList </strong>or a<strong> linked List. </strong>Check that the bill does not exist, and add it, then save the content when entering the information of the added bills is finished.</li>

   <li>Opens the txt file and reads its content to look for a specific bill (using bill number for example) and update the bill attributes (i.e. for <em>subscription</em> bill type you update subscription type for example, or for <em>service</em> bill you update the number of hours and total bill).</li>

   <li>Opens the txt file and iterate though it looking for information that match the passed parameter to this method. If any match is found, the bill must be deleted (e.g., passing supplier ID and delete the bill(s) of this suppliers).</li>

  </ol></li>

 <li>Write the code of a method calls <strong><em>findSupllierTotal Bills()</em></strong>, which calculates the combined total bills for a specific supplier.</li>

 <li>Write the code of a method called <strong><em>find Highest _and _Lowest Service(),</em></strong>which iterates through the <strong>txt</strong>, and finds the services suppliers with the highest and the lowest hourly rate, then displays the name and the service of such supplier.</li>

 <li>You must submit a UML class diagram that shows your classes, their hierarchy and their relations.</li>

</ol>







<strong>General Guidelines When Writing Programs  </strong>

<strong> </strong>

<ul>

 <li>Include the following comments at the top of each class you are writing.</li>

</ul>

// —————————————————–

// Assignment #4

//

// Written by: (include your name(s) and student ID(s)) // —————————————————–




<ul>

 <li>When commenting your code provide on the top a general and clear explanation of what the piece of code is doing; and within that piece of code if there is any method or any loop specify briefly what is doing. Include comments as needed.</li>

 <li>Display clear prompts for the user whenever you are expecting the user to enter data from the keyboard.</li>

 <li>All outputs should be displayed with clear messages and in an easy to read format.</li>

 <li>End your program with a closing message so that the user knows that the program has terminated.</li>

</ul>

<strong> </strong>

<strong> </strong>


