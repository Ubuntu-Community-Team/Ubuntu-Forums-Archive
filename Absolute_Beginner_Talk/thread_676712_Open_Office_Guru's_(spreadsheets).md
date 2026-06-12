---
title: "Open Office Guru's (spreadsheets)"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Blue_Horseshoe on 2008-01-24
Sorry, but I am a complete idiot  when it comes to spreadsheets. I can also come up with no real solid search terms to find the answer myself. Here goes...

down column A I have a list of names
down column B I have a list of numbers
down column C I have a list of numbers
down column D I want 

C of row x (minus) B of row x  = D of row x 
where x=row number

Somthing like this


nameA | 100 | 150 |[COLOR="Red"] 50[/COLOR]
nameB | 75   | 130 | [COLOR="Red"]55[/COLOR]
nameC | 110 | 100 | [COLOR="Red"]-10[/COLOR]

without doing somthing like this for each row 
```
=c1-b1 
```

I'm sure this task can be automated by some argument, I'm just to new at doing this to know how.

something like:

get x where x = row #
=cx-bx

Im sure im missing something, and even the stuff I just wrote I have no clue how to get into proper syntax.

---

### Post by Lord Illidan on 2008-01-24
It's quite easy. Just write the text```
=(c1-b1)
``` into D1.

Look at the cell's lower right hand corner, it should have a sort of small box.Drag it downwards. This activates an auto fill feature, that will fill the cells with c2-b2, c3-b3 automatically. This is also standard on Microsoft Office.

For more information, check out the help in Open Office, specifically autofill.

---

### Post by Whiffle on 2008-01-24
do 

=c1-b1   in the top cell of B, then click the cell, click the little box in the right hand corner, and drag down as far as you want to go.  

Is that what you're looking for?

---

### Post by mozetti on 2008-01-24
yeah, just copy and paste the formula from cell d1 into the rest of the cells in column d - it will automatically change the row numbers for you.

No offense meant but this is not only basic spreadsheet use, and it's very intuitive that I'm surprised you didn't figure it out on your own.

---

### Post by Blue_Horseshoe on 2008-01-24
yeah, I guess I really over complicated things, anyways, thanks for the help guys you made my day!

---

