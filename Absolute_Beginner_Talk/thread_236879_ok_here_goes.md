---
title: "ok here goes"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by llandoverysurfer on 2006-08-15
hi all
 im new to ubuntu, in fact im new to linux. for the last few days i have been trying to install another linux OS but i have had trouble getting the partitions right. i used partition magic to set up my partitions following the  instructions to set up an other OS i then installed the linux OS and got into it no problem but when i tried to boot windows again it said some of the files were corrupted. i have since as you can guess by this post formatted my HD and installed windows again. i was a bit put off trying to go for a dueal boot again but having come across ubuntu i am almost tempted to try again as it sounds like th ideal system to learn about linux on.
so my first question of many is, on a 80gb Hd how much space should i allow to ubuntu and should i use swap file for ubuntu?

---

### Post by Titus A Duxass on 2006-08-15
You need about 5-10gb for ubuntu + some for your /home, swap is normally twice the size of your RAM.

---

### Post by benuski on 2006-08-15
Well, for the size of your partition, it depends on how much you think you're going to use Ubuntu.  If you think it will be your main operating system and have lots of movies or music or things like that on it, you might want to give it most of the space on your hard drive.  Bt if you only want to use it for specific things, you might want to let windows still be the majority of the hard space.  Pretty much the place where you're going to be spending the most time should get the majority of the space.

As for a swap file, its always good to have one of at least 512MB just in case you need that extra memory temporarily.  Personally, I have a Gig of space for mine, but I don't know what the average is.

---

### Post by llandoverysurfer on 2006-08-15
ok so i use partition manager to make the new partition and the swap file? then reboot and set ubuntu to install on the partion i have just created yes?

---

### Post by kerry_s on 2006-08-15
Just to note when resizing windows always defrag windows first, windows scatters data all over the drive if you resize with out defragging that could cause the data corruption.

---

### Post by llandoverysurfer on 2006-08-15
thanks kerry i never thought of that

---

### Post by az on 2006-08-15
> **llandoverysurfer said:**
> ok so i use partition manager to make the new partition and the swap file? then reboot and set ubuntu to install on the partion i have just created yes?

Just boot the installer and let it do the partitioning for you.  Avoid partition magic.  It sometimes has trouble with linux partitions.

You will be asked how much to shrink the existing partion.  It does the rest.

---

### Post by llandoverysurfer on 2006-08-15
yeah i figured that out lol well i burnt it to disk and let it run and did the partitions manually and i now havea dual boot system on my pc im well chuffed. now all i need is to get my usb accessrunner modem to work and im away :)

---

### Post by steve.horsley on 2006-08-15
> **llandoverysurfer said:**
> ok so i use partition manager to make the new partition and the swap file? then reboot and set ubuntu to install on the partion i have just created yes?

[SIZE="6"]Nooooo![/SIZE]

Don't use PM to create partitions for Linux! You don't use Linux to create partitions for Windows before installing it do you?

Just leave around 10 Gig unpartitioned, and let the installer "use the free disk space". It will make a large ext3 partition and a suitable size swap partition, and will format them correctly. Easy.

Edit: Oops, you've already done it. I should have read to the end of the thread. Oh well.

---

