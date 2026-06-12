---
title: "Spread Sheet Column Sorting"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by gary1163 on 2007-11-12
Hello, I having a hard time trying to sort two list columns a spread sheet (using Staroffice8) for example:


1. 2 FAST 2 FURIOUS	6. Blievers					 				
2. 8 MILE		7. BIG MOMMA'S HOUSE 2					 					
3. 16 BLOCKS	8. BILL COSBY (HIMSELF)					 						
4. 25TH FLOOR	9. BILL ENGVALL					 						
5. 28 DAYS LATER	10.BLACK SNAKE MOAN	


HOW DO I GET THESE TO STAY ALPHABETIZED? MY ACTUAL LAYOUT IS 
35 ENTRIES PER COLUMN, A TOTAL OF 70 PER PAGE...

THANKS

---

### Post by K.Mandla on 2007-11-14
Moved to Absolute Beginner Talk.

---

### Post by Rhubarb on 2007-11-14
You can sort data in OpenOffice (which would be very similar to Star Office I think) by highlighting the column, go up to the Data menu, select Sort, make sure the column is specified, and that it's in ascending order, then press ok.

Because you have your data in 2 columns, you would only be able to sort one column at a time, which won't work for you because Star Office (or OpenOffice for that matter) wouldn't know that you want to sort both columns of equal row length.

Maybe you should think about using a database instead?
Or maybe programming a macro to sort it out better?

---

### Post by gary1163 on 2007-11-14
yeah if it was only a single column I would be golden,thanks  for the info, but how would Ii go about using a data base instead, any hints,instructions would be helpful...

---

### Post by Rhubarb on 2007-11-14
Sorry I can't really help you with databases, as I'm just learning them myself.
The Database in OpenOffice should be able to do it fine.

---

### Post by Hampster on 2007-12-06
I think I have a similar problem.  I have two columns; 
A is full of stock codes in descending alphabetical order and 
B is full of prices that are all over the place.  

I want to sort Column B into descending order and have the corresponding Stock code go with the prices.  That is locking the selection across the columns and sorting by one column.  
Any clues???

Using OpenOffice.org Calc

---

### Post by mozetti on 2007-12-06
Not on my Ubuntu PC right now, but in MS Excel it requires you to highlight **all** the columns in your table before you do a sort, otherwise your data integrity is lost. Using [Hampster's[/b] example, if you only highlight the "prices" column only and sort it, then the prices will sort in descending order, but the "stock codes" column won't changes -- meaning your "stock codes" don't match up to their "prices" any longer.

In this example (and using MS Excel - not sure about OO.o), just highlight columns A & B ("stock codes" & "prices") and then sort column B, descending. That would move the "stock codes" with the "prices' when they are sorted. Probably works the same in OO.o, but I haven't tried it yet.

---

### Post by Hampster on 2007-12-12
Thanks Mozetti.  That gave me the clue.  I selected both columns and then went to Data Sort and selected Column B and it worked.  In Excel I was prompted to "Extend the selection" Org doesn't have that prompt.  Thanks it worked as above.  Ta.

---

