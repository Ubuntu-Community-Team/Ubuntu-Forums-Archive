---
title: "[SOLVED] Hard disk partition size"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Jim_in_Germany on 2008-04-07
Morning,

Where in Ubuntu can I see how much of my hard disk is taken up with Ubuntu?
The equivalent of My Computer - properties in Windows which displays a nice pie chart telling you how much free disk space you have.

Cheers
Jim

---

### Post by tamoneya on 2008-04-07
system ->administration -> system monitor
Go to the tab called file systems

---

### Post by bumanie on 2008-04-07
Applications --> Accessories --> Disk Usage Analyser Then click on file systems and it will show up space is taken up by which parts of the system etc.

---

### Post by apothecaryaaron on 2008-04-07
Click Places -> then Computer.

Right click any hard drive or partition -> Click Properties.

There are the pie charts.

---

### Post by Jim_in_Germany on 2008-04-07
Thank you both. Exactly what I wanted.

---

### Post by Belak on 2008-04-07
Applications->Accessories->Disk Usage Analyzer

OR,

Open
Applications->Accessories->Terminal

And type in
df
and hit enter

Cheers!

---

### Post by SlappyPappy on 2008-04-07
Who doesn't like pie?

Neat to remember. Man, still so much to learn. 

It's funny too how we have to have what we know from other systems like pie charts in Windows. I never knew there were pies in Windows. 

Guess I wasn't hungry enough!  :confused:

---

### Post by tommcd on 2008-04-07
From the terminal you can do:
"df -h" 
this will show you each partition and the percentage used in each.
This will work on any distro.

---

### Post by Jim_in_Germany on 2008-04-07
Now that's neat. Very concise

---

