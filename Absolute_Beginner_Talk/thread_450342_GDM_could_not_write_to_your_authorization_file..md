---
title: "GDM could not write to your authorization file."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-21
I tried to log in to my Ubuntu Feisty and I get:

GDM could not write to your authorization file.  This could
mean that you are out of disk space or that your home
directory could not be opened for writing.  In any case, it is not
possible to log in.  Please contact your system administrator.


Before I screw this up, I would like some suggestions.  I did boot the recovery console and did a df -h and noted that the root partition is at 100%.  Hmm, how can that be - I don't recall loading anythiing.

Carl

---

### Post by apjone on 2007-05-21
try a du -h from inside /var 

It may be var is full.

If not is /home on the same partiton as / ?

---

### Post by justleen on 2007-05-21
when you get the message, go to a terminal (CTRL-ALT-F1) and login

delete your /home/user/.Trash/* , to get some space (assuming that every thing in your trash can go, and assuming there is stuff in there :))
that should free some space so you can get into the GUI.. after that you can use the disk analyzer to anylyza what is filling your system

---

### Post by cwmoser on 2007-05-21
I have nothing in .Trash, nothing in /tmp.  I did not install any apps.

I uninstalled gnucash and monodevelop but still get 100% Use on /

My root partition /deve/sda3 shows size=13G, used=13G, Avail=0

Almost sounds like a virus

It was working fine yesterday.

Carl

---

### Post by cwmoser on 2007-05-21
Thanks for the ideas.  It was simply that I had run out of disk space.

As suggested, I Ctl+Alt+F2 to get a console login.  Then logged in as me, and then sudo to root.
Found some stuff and deleted it.  At first, what I deleted still reported 100%.  Then I went looking for some big items and rm /usr/src which got me down to 79%.

Being relatively new to Linux, it would be nice to know about what relatively large packages are not that critical and can be removed.  I cleaned /tmp and checked ~/.Trash but beyond that I was not sure.

Carl

---

### Post by justleen on 2007-05-21
Just as a tip, start Disk Analyzer and analyse your system root.
This will give you a graphical view of what folders are the biggest ones. that might help in getting an understanding of what is where.

/var/cache can contain alot of data aswell, since  /var/cache/apt/ is used for all your downloaded and installed files.

the /usr/src/ was your kernel source code.. you might need that again some where in the future :)

---

### Post by cwmoser on 2007-05-21
Thanks for the tip about Disk Usage Analyzer.

I ran this and found that /var is 5.8GB with /var/log at 5.4GB.

So, can I safely delete /var/log/* 

Carl

---

### Post by apjone on 2007-05-21
find out where in /var/log/ the space is used by using 
```
du -h /var/log 
```

---

### Post by apjone on 2007-05-21
This will tell you which progam and sort the problem out

---

