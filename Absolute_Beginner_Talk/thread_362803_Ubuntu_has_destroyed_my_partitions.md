---
title: "Ubuntu has destroyed my partitions?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Spo8 on 2007-02-16
Edit: Wow, in a bizarre coincidence, it turns out that one of my cables must have come loose as I reset after the installation, because after opening it up and re-plugging both end of the SATA, it's working fine.  Thanks for your responses anyway!

---

### Post by shareMenaPeace on 2007-02-16
Can you start the gnome partition manager and make a screenshot from your harddrives?

You can start by accessing system -> administration -> gnome partition manager

---

### Post by thenetduck on 2007-02-16
Hi, 
  Ok if you need to get to your windows files and the live cd doesn't mount them, use this tutorial to get to your windows files (This should help you get through tonight) 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Ok, I really don't know why you got the error you did. It sounds like you might have a problem with your GRUB boot loader. Have you tried to install the OS again? Make sure you are installing the GRUB boot loader on the MBR (Master Boot Record). 
  Are you letting Ubuntu auto partition your hard drive and set things up? or are you doing it manually? 
   
  Try doing it manually, if that doesn't work try letting Ubuntu set everything up. Also, check your cd to see if it did a "bad" burn, or is a bad copy. 

 I some of this helped , 

 The Net Duck

---

### Post by Spr0k3t on 2007-02-16
Since your concern is focused on retrieving information on the hard drive, what I would do is focus on fixing the MBR (master boot record) before doing any other writing to the drive.  Do a search for "fixmbr".  I've never had to use it so I couldn't give you a better detail on what needs to be done.  One important note, when setting up a system that alters the partition information, it's benneficial to make backups of critical data first.  I guess it's something you can chalk up to experience now I suppose.

Anyway, best of luck and I hope I've pointed you in the correct direction.

---

### Post by ndefontenay on 2007-02-16
There something I'm not quite sure of in your description.

Is your windows and Linux installed on a different disk or simply in different partitions on the same disk?

Since you focus on recovering, I would suggest that you plug your hard disk on a working OS (Either at a friends or by installing Ubuntu on another disk quickly) and then mount this disk to access the data on the new OS.

Then, when you got your data backed up, you can do whatever you want with your partition.

regards,

Nicolas

---

### Post by Spo8 on 2007-02-16
Thanks for that, but I actually got it fixed and edited the OP.  Honestly, what are the chances of that happening?

---

