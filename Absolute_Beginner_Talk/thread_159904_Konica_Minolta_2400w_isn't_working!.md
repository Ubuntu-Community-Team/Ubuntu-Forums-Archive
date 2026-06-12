---
title: "Konica Minolta 2400w isn't working!"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by doonavin on 2006-04-13
I'm converting all my home PC's over to Linux, and have been having a pretty easy time until now...

My printer died, and since I'm sick of buying disposable deskjets, I decided to go with a color lazer for the long haul.

I did research before I bought, and there is a driver (m2300w).

Problem is that I followed the install instructions to the letter, and when I try to set up the printer in the cups gui, there is no Konica Minolta group.  So I specify the ppd file, and it installs the printer.  If I try to print  a test page... I get nothing.  If close the window and then redisplay the printer properties, it always goes back to a minolta magicolor 2430 DL driver.

Getting VERY frustrated!! Please help!!!

I don't really know how to troubleshoot the printing systems... 

Does anyone know where I can find a dep package for it?

---

### Post by taladon on 2006-07-01
Hi.
I'm in the same boat as you.
I downloaded the 2300w driver just like you did.
I tried using alien to install the rpm, but it gave the following errors:

root@bigbox:~# alien -i m2300w-0.51-1.i386.rpm
dpkg: error processing m2300w_0.51-2_i386.deb (--install):
 trying to overwrite `/usr/share/foomatic/db/source/driver/m2300w.xml', which is also in package foomatic-db
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 m2300w_0.51-2_i386.deb

Any help from senior linux gurus is much appreciated!

--Taladon

---

### Post by taladon on 2006-07-23
Hi all!

I'd like to give an update about my current printer status:

I am running Ubuntu 6.06 with all updates.
I downloaded & installed the latest cups release, 1.3 directly from cups.
I then downloaded 8 installed the 2300m driver from sourceforge

Now I am able to print sometimes. It takes a really long time (10-30 mins) before the printer starts, but it does actually print sometimes.

However, sometimes it "crashes" the printer with the error light on the printer and the ready light flashing. I chalk it up to the 2300m driver still being in alpha state, coupled with 1.3svn not being totally finished. 

This has given me a lot of hope about being able to go totally 100% linux one day. If you would like more info, feel free to drop me an email with subject line "2400w printer" in it so I don't miss you by accident.

Well, till next time rock on!

--Taladon

---

### Post by taladon on 2006-11-05
Hi, it's me again.
I've got my printer working now.
Details here: [http://www.ubuntuforums.org/showthread.php?t=255490&highlight=minolta](http://www.ubuntuforums.org/showthread.php?t=255490&highlight=minolta)

Have fun
--Taladon

---

### Post by rhyshowitt on 2007-04-21
Wahoo!! The Konica Minota 2300W loads under Feisty Fawn!  I had to download m2300w-wrapper, which was easy using Synaptic, then with just a little playing around it worked.  Well.

Looks like it will do the same for the 2400W.

Rhys

---

### Post by isecore on 2007-11-06
> **rhyshowitt said:**
> Wahoo!! The Konica Minota 2300W loads under Feisty Fawn!  I had to download m2300w-wrapper, which was easy using Synaptic, then with just a little playing around it worked.  Well.

Looks like it will do the same for the 2400W.

Rhys

Thanks for that! 2300w-wrapper was what was missing to make my 2300w working. After I added that package everything worked peachy.

---

