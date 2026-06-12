---
title: "&quot;Error Loading Operating System&quot;"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Fatsobob on 2006-08-09
After installing Dapper Drake on my computer on a 160gig slave drive, I get this error message that says "Error Loading Operating System" when it is going to boot. I have installed using 2 different disks of the regular and the 64bit version and I get the same mistake each time. Some help is required because I need this to access my windows partition.

---

### Post by Fatsobob on 2006-08-09
I pastebin'd my menu.lst and by looking at it, it looks pretty fine to me.
[http://pastebin.ca/124126](http://pastebin.ca/124126)

---

### Post by Aikon- on 2006-08-09
Hi Fatsobob,

First, its a little bit of guesswork without a complete hardware description. I had a similar problem when installing Ubuntu 5.04 the first time around. After some research, what I decided to do was boot into my Knoppix LiveCD and use QtParted to set my Windows XP partition (NTFS) to "Active" (Windows doesn't like playing nicely ;)). After this, GRUB booted no problem.

However, after I did this, I was only able to boot into Windows; I don't know whether you will have the same problem or not, but the Ubuntu installer had listed my Linux partition as (hd1,1) when it should have been (hd0,1), so I just changed it and that fixed that problem too (just a heads up in case, after setting the NTFS partition as active you get an "ERROR 22: No such partition").

I posted a bug here: [https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/19026](https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/19026)

I hope this helps, let me know how it turns out!

---

### Post by Aikon- on 2006-08-09
p.s. when installing SuSE, it didn't change the active partition, which is why I didn't have any trouble with that

p.p.s. when installing Dapper Drake, it also didn't change the active partition, so I didn't have any trouble with that either (of course it still mislabeled my partition as (hd1,1) but that's trivial to fix, and you can even do it right in GRUB without a reboot).

---

### Post by Fatsobob on 2006-08-09
I do not have a working burner right now, so is there a partitioner I can use on the live cd? I tried to get QTparted to work and it says it can not find any drives because I am not root. Any suggestions?

---

### Post by Fatsobob on 2006-08-09
ok New problem. I was reinstalling it again, no changes made at all, and now it says "grub" at boot. Any thoughts?

---

### Post by Aikon- on 2006-08-09
Sounds promising.. do you get the menu at all? (I don't know about the live CD, I haven't used it too much)

---

### Post by Fatsobob on 2006-08-09
I don't even make it to the menu, it happens where grub would load.

---

### Post by Aikon- on 2006-08-10
Hmm.. I don't know =/

Out of my league. I would mess around with stuff and try to track down the problem but can't really do that without the hardware.

Good luck!

---

### Post by p0rk on 2006-08-15
Having the same thing happen to me at the moment, running 64bit version the workaround Im using at the moment is to boot off the Cd and select boot from first hd, Ill try to set windows as active when I get home =]

---

### Post by stalker145 on 2006-08-15
fatsobob, 
As said before, not knowing much about your setup, the only thing that I can think to say is refer you to how I [fixed the problem]("http://www.ubuntuforums.org/showthread.php?t=202640") when I had it.
Good luck getting up and running. Let us know how it turns out.

---

