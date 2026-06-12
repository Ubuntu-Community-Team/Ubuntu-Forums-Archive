---
title: "In Ubuntu / Linux- where are the &quot;executable files&quot; for the applications ?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by brjoon1021 on 2008-03-31
HI,

I just installed Multiget from synaptic to be my download manager. I have the Flashgot extension of Firefox which allows you to select download managers installed or to add one.

Well, I tried to add multiget because it was not on the list and I need to be able to find the "executable file" for multiget in order to be able to use it.

Thanks,

B

---

### Post by leg on 2008-03-31
probably /usr/bin

If you don't find it there look for the bin directories bin stands for binary. There are /bin /usr/bin /usr/local/bin

---

### Post by dannyboy79 on 2008-03-31
did you do a search for it? first issue

sudo updatedb

that will update your slocate database, then issue this command

sudo locate multiget

and hope that it's named that. it should be within /usr/bin/.

---

### Post by Whiffle on 2008-03-31
Easiest way to find it is to open open up a terminal and type

which  nameofapplication


It will return the path.  Usually though, but not always, applications are stored in /usr/bin, /usr/local/bin/ or some other variant.  Also, somtimes they get put in /opt

---

### Post by tech404 on 2008-03-31
try 

sudo updatedb
locate -i 'MultiGet'

it should tell you where it is

---

