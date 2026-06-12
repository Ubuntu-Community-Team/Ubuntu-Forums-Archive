---
title: "Dual-booting SUSE and Ubuntu"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by napnip on 2006-03-15
OK gang, I hope this is the right forum to post this question in.

I dual-boot SUSE 10.0 and Ubuntu 5.10.  (I like features of both.)  You'll be glad to know that I ditched Windows entirely, but that's another topic for another thread.  ;) 

My question is this:  How can I access my SUSE partition from within Ubuntu?  I've got a 160 gig drive and a 20 gig drive.  The 160 is dedicated to SUSE while my 20 is dedicated to Ubuntu.  However, I would like to be able to access some files on my 160 gig drive from within Ubuntu.  Is this possible?

When I navigate though the directory structure from within Ubuntu, I don't see my 160 gig drive.  (Maybe I'm not looking in the right place?)

Any help is greatly appreciated!  :-D

---

### Post by evilgold on 2006-03-15
you have to mount it first.

sudo mount /dev/hda1 /mount/folder

replace hda1 with the hd and partition suse is on, and /mount/folder with the folder you'd like it to mount to.

You could also add it to /etc/fstab to have it mount automatically on boot

---

### Post by napnip on 2006-03-15
Many thanks!!!!!!  :KS

---

