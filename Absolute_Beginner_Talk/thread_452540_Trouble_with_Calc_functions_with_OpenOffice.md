---
title: "Trouble with Calc functions with OpenOffice"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-05-23
Hello out there

I have recently made the switch from XP to Ubuntu and find it very stable and want to continue using it. My only problem is making Open office do VBA macros (although it's getting better) and 1 other problem I have. I tried the OpenOffice forum but no one has answered.

My problem is I have a workbook with 2 worksheets. 1 an order form and one an invoice. I would like to be able to display only items ordered from the order form on the invoice rather than the sloppy way I have it right now where everything is displayed (even items not ordered).

I know this probably isn't the right place to post this but if anyone can help or even re-direct me to a place that can, I would be grateful

Thanks

---

### Post by laidback on 2007-05-23
How do items not ordered get on the invoice?...must admit I don't really understand the problem too well. Can you explain a little further.

---

### Post by eekfonky on 2007-05-23
I use" =Concatenate(workbook_ref,cell_ref)" for strings and simply "=workbook_ref,cell_ref" for the numbers.
The problem is I have to copy across all the products so as to get the ones that are ordered.

---

### Post by laidback on 2007-05-23
OK, think I understand. I now believe that I understand what your order form is, a complete list of available items against which you may put a tick to indicate "Buy this item", then you want the invoice to list only those items with a tick against them. Yes?

I'll think about this and get back to you (it's rather late now)....no guarantees...but it will be possible.

Laidback

---

### Post by laidback on 2007-05-24
Any chance of you emailing me a copy of your order form and invoice, just an example would do.

---

### Post by laidback on 2007-05-25
A simple solution would appear to be as follows.

Imagine that your Invoice sheet has 3 columns called :-

```
Item	Description	No required

```

and underneath you have all the possible items, as indeed you have at present:-

```
Item	Description	No required
1	item 1	                1
2	item 2	
3	item 3	
4	item 4	
5	item 5	
6	item 6	
7	item 7	
8	item 8	
9	item 9	
10	item 10	
11	item 11	
12	item 12	
13	item 13	
14	item 14	
15	item 15	
16	item 16	
17	item 17	
18	item 18	
19	item 19	
20	item 20	
21	item 21	
22	item 22	
23	item 23	
24	item 24	
25	item 25	             1
26	item 26	             1
27	item 27	
28	item 28	
29	item 29	

```

in the No required column you see we have a 1 against items that are required. Now using :-

Data>Filter>Autofilter

I can select in the No Required column (click on the arrow) non empty...this results in a list where only the ordered items are listed:-

```
Item	Description	No required
1	item 1	                 1
25	item 25	                1
26	item 26	                1

```

this list can be printed as is, the hidden lines will not be printed.

Now I know that this is possibly not exactly what you had in mind, indeed it is probably no where near the best solution but, it doesn't require knowledge of visual basic which is what you need for writing/modifying macros. I did create a macro but it seems so far away from my knowledge of Excel macros that I would need to spend a lot of time learning this new language before I could attempt a solution.

If I were doing this for real I'd probably look at having just an invoice, select what you want as per my example, autofilter it, print, remove the auofilter, clear the No Required column and start again. Most, if not all, of this could be attached to macros that one wouldn't need to edit. But it all depends on your requirements.

I trust that this has been of some help. I'm away for a week (from Sunday) now so cannot reliably post until June 3rd.

Please let me know what you think of the idea at least. I appreciate that it needs some work before if could be considered a live system.

Laidback

PS No required column is out of position, sorry, but you get the idea? I don't know how to copy the spreadsheet areas onto the POST

---

