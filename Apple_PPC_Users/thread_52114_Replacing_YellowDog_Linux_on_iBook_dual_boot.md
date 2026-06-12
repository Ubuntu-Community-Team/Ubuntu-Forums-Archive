---
title: "Replacing YellowDog Linux on iBook dual boot"
date: 2005-07-26
forum: Apple PPC Users
---

### Post by orlando_nick on 2005-07-26
Hi all.

Currently have a G3/800mhz iBook dual boot, OSX and YellowDog linux. After the success of running Ubuntu on my server, I'd like to replace YellowDog on the iBook.

Question is, can this be done from the boot CD setup without ruining the OSX install? I'd prefer to not have to reinstall OSX, etc.

Thanks!

---

### Post by Down8ve on 2005-07-26
You know, I did this via the Ubuntu installer.  Seems to me there were a few options when you get to the partition options.  The program will drop to a table showing the partitions of your hard drive.

I deleted the Bootstrap partition and the Linux Swap and Home(?) partitions, making them free space (which is what happens after you delete them.

I then whent back to the main partition screen and told Ubuntu to use the existing free space.

Someone please make corections if I am wrong.  I'd hate for Nick to lose important data on my account.

DSM

---

### Post by chascon on 2005-07-27
I've done it just like its mentioned.

---

### Post by autocrosser on 2005-07-27
I replaced YellowDog on my / directory--I had /home - /tmp & /opt on seperate drive partitions & just installing Ubuntu on the main directory allowed me to keep my user files intact. After installing, I went in as root user--edited my fstab & rebooted--Ubuntu "found" my drive partitions on reboot. Didn't even need to back everything up (I did anyway :-) )--Gnome updated my dot files & I was in business....

And a note--make sure to check your xorg.conf--mine listed my keyboard as "pc104"--couldn't use the numerical pad section--change it to "macintosh" and you will have full access--

---

### Post by orlando_nick on 2005-07-27
Thanks for the replies all  :) 

I'll try it this evening and let you know how it turns out. I hadn't used YellowDog much since I ran into a few glitches... so there's not much to lose by just wiping it out.

---

### Post by orlando_nick on 2005-07-27
Well, booted from the Ubuntu CD, ran an install but after the boot screen (choice of linux, osx or CD), ended up at a boot prompt. I booted from the OSX CD after that to 'erase' the bootstrap and hosed the whole OSX install  ](*,) 

All's not lost. At least now I can configure the partition sizes better and have a fresh Tiger install  \\:D/ 

Thanks again for the help. I'll post the results when all is done.

---

