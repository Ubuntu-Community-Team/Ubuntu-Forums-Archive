---
title: "Open office issues - losing data in calc, it moves across etc"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by daniel@dpr on 2005-07-06
Hello,
I might be going crazy.
Im having a lot of issues with Open office, especially calc.

I use office to sort out large amounts of data, i open tabdelimited files in gedit (love that by the way, great for php code pages), and try and copy and past them into calc. There is where i manipulate things for import into my website DB.

My problems started when i tried to copy and past it into calc. i was losing the first 10 lines or so of data, then i opened a new worksheet (same workbook) and it pasted/imported fine. Then i delete everything and try again and it happens again (bits go missing).

I also cannot right click the tdl file and select openwith calc, it starts to then the file opens in writer instead. OK i can live with that, strange nonetheless.

Now, when i do get a worksheet started, and the top row represents column headings, i start entering data below and things go missing, or it moves. strange as it sounds i enter data starting at A2, then work across to say w2, i use the scroll bar to get back to A3 and the data in a2 is gone, its shifted across several cells.

In the meantime i have to go in the other room, and work on my xp machine, i hate that, as this is the major glitch in my ubuntu/linux move, everything else i love!.


is there any opinions as to what im doing wrong? im using version 2 of openoffice, upgraded using synaptic package manager.


Thanks

---

### Post by varunus on 2005-07-07
OpenOffice 2 is beta software; you may actually want to report these issues that you're having.  (Sounds like a bug to me.)  Until then, OpenOffice 1.1, which should still be installed as OpenOffice 2 doesn't overwrite it, should work for you.

Good luck.

---

### Post by poofyhairguy on 2005-07-07
Honestly calc is quite lacking. You need gnumeric.

> sudo apt-get install gnumeric

Its the best spreadsheet software in Linux.

---

### Post by sonny on 2005-07-07
I also recomend gnumeric, I work with a big amount of data for university work, and I was having some troubles with calc, but gnumeric seemed to fix them all, and is more like MS-Office.

---

### Post by daniel@dpr on 2005-07-08
[QUOTE=sonny]I also recomend gnumeric, I work with a big amount of data for university work, and I was having some troubles with calc, but gnumeric seemed to fix them all, and is more like MS-Office.[/QUOTE]

Firstly, thanks, I dont think i have been on a forum that is so positively responsive.

I am not trying to sound ungrateful.
But.

Boy am I having some dramas. Gnumeric is a lot better, but crashed constantly when i tried to import csv files where the seperator was a "|" (pipe) as one of my pricelists comes in that format. It imported Tad delimited files fine.

The workaround was open it in Open Office (that actually worked) then sort the columns out, copy and paste that into gedit then copy and paste that back into a gnumeric worksheet.

I tried saving the OO file as a CSV, and it wouldnt work, i mean the file wouldnt save, i couldnt find it!!! If i tried to save it as an .xls in OO it would save 10% of the file, and leave out the rest of the info.

Lots of things are unlike MS Office that were critical to me. First is when i sort a column of data, (A-Z) it doesnt grab the data (or think the data is related) either side, or the whole worksheet, which means prices for products are all over the place, I did find a work around, by manually selecting every column then deleting all but the one i wanted sorted (this is an automatic function in msoffice).

Second major issue for me was the auto filter option. It works, but when i enter data in a cell alongside it, it doesnt follow suit when i unfilter it. What i mean is i want to say grab a subcategory of products (defined in say column b) then put/change the home/parent category in the cell next to it (column A) then "unfilter" the result, the "A" cells end up anywhere but next to where i wanted them, or initially put them.

These issues im going to take up with, or report as bugs, to the developers of the respective programs, I just wanted to voice my opinions here, as I think its important, for those relying heavily on office programs.


I am however determined, to stay with Ubuntu. Its great in nearly every other application. I just hate the fact that a MS product is better (dont beat me for that comment) albeit in my scenario it is. Did i break any forum rules with that comment? sorry.

Hopefully they are simple issues, fixable by the developers.

Oh and even with the issues, both gnumeric and OO 2.0 were better in many ways than MS office 2003. The fact for instance, that i can import (ok it didnt work but the idea was there) a file and CHOOSE THE DELIMITER!!! (something unavailable in msoffice) is very impressive. Some of my files are commer seperated, some are tab, some the "pipe" character (|)

Please dont consider this an unappreciative rant, I have no idea as to the effort involved in a project like Ubuntu, or OO, or gnumeric, as you can tell with my posts, I just want to post this to hopefully save someone else in my position a similar problem (and wasted days).

Thankyou all again, 

Daniel

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=daniel@dpr]
I am however determined, to stay with Ubuntu. Its great in nearly every other application. I just hate the fact that a MS product is better (dont beat me for that comment) albeit in my scenario it is. Did i break any forum rules with that comment? sorry.[/QUOTE]

No. You are cool, its just honesty. Nothing we have is as good as Excel. Just try to file a bug report please.

---

