---
title: "question about partition sizes"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by philmiller on 2007-02-05
My question is about partition sizes.  I installed Ubuntu as a duel boot along with XP.  I manually configured the partitions so that I have:

[LIST]
[*]windowsxp (ntfs) 70gb
[*]shared data (fat32) 8gb
[*]/home (ext3) 1 gb
[*]/root (ext3) 3gb
[*]/swap 512 mb
[/LIST]

My understanding is that it is recommended to have /root be about 2-3 gb.  Well after using Ubuntu for only one week I can now not log in because /root is full (I think it said that it is unable to write my session becuase /root was full).

What is the easiest way to make this work (log into ubuntu)?  Should I remove all the partitions that I created for Ubuntu and replace them?  And if i do this what size should i create the partitions?

Or is there a way to resize these without starting from scratch.  If it is easier to start from scratch I might just do that since I really won't lose anything, just a few settings for FireFox.

Also is it necessary to have to log into Ubuntu **every **session?

If you need more information please let me know.  I am never sure what I need to include so that I can get the correct answer.

Thanks in advance for all the help.

Phil

---

### Post by taurus on 2007-02-05
When you say /root I assume you mean /.  You need about 2.5GB if you install Gnome so 3GB is enough, assuming you don't install anything else.  Therefore, I think 5GB is probably what you would like to have for /.

---

### Post by Ryan450 on 2007-02-05
/ does have a nasty tendacy to fill up really quick. 

as for a quick fix I dont know of one, so I'd suggest reformatting and redoing your patition table. 

my ubuntu partitions are like this..

/ - 4 gb
/swap - 1 gb
/home - 10 gb
/usr - whatever is left over.

most programs that you install will be put into /usr where theres lots of space. if you dont give its own partition then by default all your programs are installed into /.

Hope this helps.

---

### Post by philmiller on 2007-02-05
> **Ryan450 said:**
> / does have a nasty tendacy to fill up really quick. 

as for a quick fix I dont know of one, so I'd suggest reformatting and redoing your patition table. 

my ubuntu partitions are like this..

/ - 4 gb
/swap - 1 gb
/home - 10 gb
/usr - whatever is left over.

most programs that you install will be put into /usr where theres lots of space. if you dont give its own partition then by default all your programs are installed into /.

Hope this helps.

Excellent.  

> most programs that you install will be put into /usr where theres lots of space. if you dont give its own partition then by default all your programs are installed into /.

that I think is my problem.  all my programs were being put into /

yes i mean / when i write /root (that is what i thought it was called)  I am n00b hear me roar!

---

