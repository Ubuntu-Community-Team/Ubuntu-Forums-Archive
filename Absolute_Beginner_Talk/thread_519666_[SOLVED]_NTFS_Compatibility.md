---
title: "[SOLVED] NTFS Compatibility"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by tzmeddy on 2007-08-07
Hi guyz!
Im new  with  this  Ubuntu  thing but  so far i love it.install was   smooth  though i had  to do some research  about  partitioning  and  setting up  GRUB to boot to my  default  OS.
So yesterday  i  did  some  updates  for  Ubuntu  and all of  the  sudden  im able to  read  from  my  external  USB  harddrive which is partitioned in  NTFS.Plus  the  fact  that i  didnt  have to install  any drivers  for  the  USB connection. This is   nice   thing for me. I hope  it  does the  same thing  for my all in one  printer HP.If not  then  i  will  ask for help  from you citizens of  Ubuntu.

---

### Post by Inxsible on 2007-08-07
Welcome to Ubuntu. 

You might however, wanna have a look at ntfs-3g which needs to be installed in order to gain write access to NTFS drives.

---

### Post by tzmeddy on 2007-08-07
> **Inxsible said:**
> Welcome to Ubuntu. 

You might however, wanna have a look at ntfs-3g which needs to be installed in order to gain write access to NTFS drives.


Ok! I appreciate  the  help. I will keep this in mind  cause  at  the  time  being  im not  concerned  about writing  on the  NTFS  drive. I m  looking  forward  to  enjoy  this  whole   ubuntu  experience.I  just  want  to  explore  the  features  available. Like  I installed   Amarok but  couldnt   play  MP3 and  failed  to install the plugin   for it. Im  using ubuntu 7.04  do  i  need  KDE  stuff  to have  this  working ?

---

### Post by Inxsible on 2007-08-07
> **tzmeddy said:**
> Ok! I appreciate  the  help. I will keep this in mind  cause  at  the  time  being  im not  concerned  about writing  on the  NTFS  drive. I m  looking  forward  to  enjoy  this  whole   ubuntu  experience.I  just  want  to  explore  the  features  available. Like  I installed   Amarok but  couldnt   play  MP3 and  failed  to install the plugin   for it. Im  using ubuntu 7.04  do  i  need  KDE  stuff  to have  this  working ?

Take your own sweet time :)

When you installed Amarok, it installed all the required KDE packages too. What you do need is to install codecs to run the mp3 and other audio video files.

Go to Applications --> Add/Remove. Search for "gstreamer" without the quotes. Install all the GStreamer codecs that you find. You should then be able to play your music.

---

### Post by GCCC on 2007-08-07
> **Inxsible said:**
> Welcome to Ubuntu. 

You might however, wanna have a look at ntfs-3g which needs to be installed in order to gain write access to NTFS drives.

Hello; I'm new to Ubuntu as well.  One of the problems that I'm having is accessing my NTFS formatted internal HD.  I have Ubuntu on a separate drive and the NTFS drive still contains my Windows installation and my other files.  I can read the drive, but cannot write to it.  I tried the ntfs-3g program, but the radio button in the program to allow write access to internal drives was grayed out.

Do you have any idea why this won't work?  Thanks in advance.

---

### Post by Inxsible on 2007-08-07
how did you install ntfs-3g ?

---

### Post by stchman on 2007-08-07
> **tzmeddy said:**
> Hi guyz!
Im new  with  this  Ubuntu  thing but  so far i love it.install was   smooth  though i had  to do some research  about  partitioning  and  setting up  GRUB to boot to my  default  OS.
So yesterday  i  did  some  updates  for  Ubuntu  and all of  the  sudden  im able to  read  from  my  external  USB  harddrive which is partitioned in  NTFS.Plus  the  fact  that i  didnt  have to install  any drivers  for  the  USB connection. This is   nice   thing for me. I hope  it  does the  same thing  for my all in one  printer HP.If not  then  i  will  ask for help  from you citizens of  Ubuntu.

Ubuntu can read NTFS out of the box no problem.  If you wish to write to NTFS then you will need to install ntfs-3g.  I have a procedure laid out that explains this.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Hope it helps.

---

### Post by GCCC on 2007-08-07
> **Inxsible said:**
> how did you install ntfs-3g ?

I just installed it using the Add/Remove manager.  I haven't tried any configuration on it yet.  It's one of the several things that I noticed that needs to be tweaked since I installed Feisty this past weekend.

I'll try the procedure that stchman posted the link to and post back with results.  (I'm not at home right now, so I can't do anything with it at the moment.)

Thank you to both of you!

---

