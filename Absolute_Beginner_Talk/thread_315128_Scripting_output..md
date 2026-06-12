---
title: "Scripting output."
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-12-08
I have been playing with scripting.  Absolute beginner.  Much fun, but a bit frustrating.

Right now I have a very simple problem, but the solution escapes me.

I can run the top command from a tty terminal and get a nice display.  If I put the command 
top -n 1 > /home/marvin/Desktop/pcinfo.txt
in a bash script I get the same output only non-ascii characters make it virtually unreadable. 

Question:  How do I instruct the bash script to ignore non-ascii characters; or convert them all to spaces?

P.S. -- I hope you consider a newbie's efforts to learn scripting as part of the Linux absolute beginners process.

---

### Post by IYY on 2006-12-08
I don't know how to do what you're asking for, but the 'cat' command will print it to the screen properly:

```
top -n 1 > /home/marvin/Desktop/pcinfo.txt
cat pcinfo.txt
```

---

### Post by Banderas_12 on 2006-12-10
You can use -b(batch) option like
top -b -n 1 > filename.out

---

### Post by OldDogNewTricks on 2006-12-10
:D Thanks Banderas_12!  Using the batch option did the trick.  This will be a good one to remember because other commands give non-ascii output too.

---

