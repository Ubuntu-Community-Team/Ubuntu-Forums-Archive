---
title: "how can i see the exactly date when i've installed my ubuntu?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-05-27
is there a way?](*,)

---

### Post by skippy81 on 2006-05-27
Well this is hardly a 'professional' way of doing it, but assuming you havn't played with your system too much you can just use the date of a file or folder which you know was created at install, but not modified since.  


Open a terminal and type:- 

> ls -l /root/Desktop

The date given for me is the day I installed my linux distrobution, this works since i know for a fact I havn't used my root account for logging into xwindows, and that the root folder itself was created during intall rather than being copied straight from the CD.  

This is obviously a poor way of doing it, so hopefully someone will suggest something better.

---

### Post by Rinzwind on 2006-05-27
How about:> 
rinzwind@discworld:~$ uname -a
Linux discworld 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

It's the last time the kernel was built (and normally you don't do it that often ;) )

---

### Post by the_nomad on 2006-05-27
i've done that:

> thbk40zu@thbk40z:~$ uname -a
Linux thbk40z 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux


but is very weird because i've installed my linux yesterday...:-k :-k :-k :-k

---

