---
title: "using terminal"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by oceanp on 2006-03-05
Hi, 
I have a 5 line command to type in terminal.  This is the first time I have used the command line.
How to I get to the next line?  When I hit return it tries to execute the line I typed.
TIA

---

### Post by Q4U on 2006-03-05
Type the "backslash" character (i.e. this: \) to avoid executing your commands when hitting Enter. 

Q

PS You might want to check out a few resources on learning the basics of the command line. I recommend the Linux Documentation Project guides called "Linux: a Hands-On Guide" and "Bash for Beginners" (downloadable free and in many different formats at: http:\\[www.tldp.org](www.tldp.org))

---

### Post by MrDan on 2006-03-05
I was looking for something like this too.

Cool link for Hands on guide.

---

### Post by oceanp on 2006-03-05
Thank yo so much for the prompt reply.

---

### Post by xhie on 2006-03-05
Yeah the easyest way to do it would be to create a small bash script and just run that

---

### Post by IYY on 2006-03-05
If it's one command split over two lines, use the slash as suggested above

[B]echo Linux \
> Rocks[/B]

will print out "Linux Rocks".

If you have two seperate commands you wish to run one after the other, use the semicolon:

**clear ; echo "Linux Rocks"**

will clear the screen, then print out "Linux Rocks"

---

