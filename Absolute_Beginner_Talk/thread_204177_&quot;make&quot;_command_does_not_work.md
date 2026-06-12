---
title: "&quot;make&quot; command does not work"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-26
Hi, 

I've tried using some of the code around here but the *make* command doesn't work:

[I]root@Ubuntu:~/ndiswrapper-1.7# make
bash: make: command not found[/I]

Any suggestions?  Thanks

---

### Post by Jasper Houtman on 2006-06-26
in terminal type: sudo apt-get install make

---

### Post by ovimunt on 2006-06-26
Hey, thanks!!! 

Worked fine!

---

### Post by richbarna on 2006-06-26
[QUOTE=ovimunt]Hi, 

I've tried using some of the code around here but the *make* command doesn't work:

[I]root@Ubuntu:~/ndiswrapper-1.7# make
bash: make: command not found[/I]

Any suggestions?  Thanks[/QUOTE]

Why not get all the compile/install tools together ?

> sudo apt-get install build-essential

---

### Post by nameiwantistaken on 2006-06-26
Why aren't these loaded by default?

---

### Post by gr0kzer0 on 2006-06-26
> Why aren't these loaded by default?

Good question.  Seems to me, the developers expect users to only want programs that are available through Synaptic and apt-get.  Wanting to compile something is obviously an advanced procedure that they don't think your average user wants.

The fact that people have had this problem constantly since I started using this forum, and long before that too, suggests to me that the developers should have realised that a lot of people want compilation tools from the start.  It isn't obvious to a new user why the "make" command isn't working.

---

### Post by taurus on 2006-06-26
[QUOTE=gr0kzer0]Good question.  Seems to me, the developers expect users to only want programs that are available through Synaptic and apt-get.  Wanting to compile something is obviously an advanced procedure that they don't think your average user wants.

The fact that people have had this problem constantly since I started using this forum, and long before that too, suggests to me that the developers should have realised that a lot of people want compilation tools from the start.  It isn't obvious to a new user why the "make" command isn't working.[/QUOTE]
Why "build-essential" does not install by default even though it's on the CD has been discussed to dead!  Some developers claim it's for security and others give other reason about users should only use apt-get/aptitude/synaptic to install things!  Either way, it's a bunch of hot air if you ask me...  ](*,)

---

