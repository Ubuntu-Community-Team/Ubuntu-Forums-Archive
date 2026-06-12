---
title: "Mounting the windows HD Question"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by mattyb1123 on 2006-12-21
I have recently downloaded Ubuntu on the live CD, and i was wondering how do you access the information on that is already on your computer? I have been running XP for years and now i'm thinking of moving to Ubuntu. I just wondered how to access that information on my Hard drive through the live cd. I hear you have to mount the Hard drive but how do i do that. 

sorry if this has been asked before. couldn't find the previous posts. any reply would be greatly appreciated.

Matty b.

---

### Post by TooRight on 2006-12-21
Welcome to Ubuntu!! :D

This is about the best link out there for how to do that:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Actually, the entire site is an incredible "how-to" resource. Definitely one to bookmark!!

Will you be doing a dual boot with xp, both systems on one drive with the drive partitioned? Be sure to dfrag windows first and then when you go through the process of the install you can choose "Guided partitioning" and then you can choose the option to let the system "partition the largest area of unused space". It will check your harddrive and will come up with a partitioning scheme (it will leave some extra room on your windows partition as well), which of course you can adjust if you like, then once you've decided, you can choose to go forward with the partition and overwrite. The Gparted program will do all the work for ya and then start with installing ubuntu. Once ubuntu is installed, you can use it, logging in with the username "oem" and the password you gave during the install. once you have it set up as you like, then paste:

> 
sudo oem-config-prepare 


into the terminal and when your computer reboots you can finish setting it up for yourself and give it the username you choose.

Then you're good to go!! :D

Also, depending on your graphic card, you might want to check a few threads here about getting the right driver and write down the commands you'd need to get the proper one, just in case it gives you a black screen. Good luck!!

---

### Post by mattyb1123 on 2006-12-21
Is there a way to not install the Ubuntu OS but still access the information on the hard drive?  or is that what the site explains?

see i'm not sure if i want to install it yet i have a dell laptop and what i really want to do is see how Ubuntu plays mp3s and all that. 

So i guess what i'm asking is there a way to use the Ubuntu CD and access the information on the hard drive.

---

### Post by EminNew on 2006-12-21
Yes there is, and it's relatively simple. Go ahead and follow the link to learn about mounting.

---

