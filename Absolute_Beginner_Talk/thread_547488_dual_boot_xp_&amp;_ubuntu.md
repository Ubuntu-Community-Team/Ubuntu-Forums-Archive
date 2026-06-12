---
title: "dual boot xp &amp; ubuntu"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-09-10
Hi i have a lenovo 3000 c100 laptop with xp pro on it. I'm looking at doing dual boot with ubuntu 7.04. I reacon i should be alright to do the install if i just choose the first option. I am just wondering if it would work if i only have about 6 gb of free space on the xp. it is a 40 gb but most 20 taken up by windows. 
Any suggestions?

---

### Post by lisati on 2007-09-10
I don't see why 20Gb each would be a problem as long as Windows has enough breathing space for its swap requirements.

---

### Post by Dark-Angel on 2007-09-10
ok well most stuff i have on an external 60gb hhd so it would mainly just be the install of windows and ubuntu on the internal 40gb harddrive.

---

### Post by Er1ck on 2007-09-10
6gb seems a bit low...if possible I would say at least 10gb with 512mb of swap and use norton partition magic to partition your hard drive and remember to unhide your windows partition if you do use PM. Also run the live CD so you can mess around with ubuntu on your computer and see if you enjoy it and if it picks up your wireless.

---

### Post by Dark-Angel on 2007-09-10
ok well i'll get rid of things i don't need and free up some more space. it has 750 of ram so should be fine i think. I don't really now about norton partition manager and don't want to be messing around much. I've tried live and seems good but doesn't pick up wireless. i've been told i might need drivers but wouldn't be able to install them until i installed ubuntu.

---

### Post by Er1ck on 2007-09-10
yeah that's correct, you'll need to have another computer close by where you can download drivers from or you could run the live cd and open up a terminal and run lspci to see what your wireless card's model number is and everything along with lspci -n to see the location of your device then with ndiswrapper and downloading a corresponding driver from their list will you be able to fully get your wireless card up and working.

---

### Post by Tautoa on 2007-09-10
My dual boot (which I got rid of four days ago... I'm Windows free :D) used a 20GB HDD like so...
7GB NTFS partition for Windows
1GB NTFS partition solely for a Windows pagefile
2GB swap partition
10GB XFS partition for /

And that worked fine for me... although I should point out that my /home partition was stored on a separate, 80GB partition, and in the end, I only installed about 6 programs on the Windows partition (a set of small, lightweight tools for modding Motorola phones)... so that perhaps explains why I got away with using so little space.

I also found that by keeping /home separate from the OS, you can reinstall the OS fairly easily, so I changed my partitioning system a couple of times before I arrived at this one. Experiment a bit until you find something that works for you, you can use GParted to resize things if you start to run out of space.

---

### Post by Dark-Angel on 2007-09-10
ok i'll try and play around then and see what works. I'll free up some space, and i think use the partion on the live cd as i don't feel good about any other.

---

### Post by Sef on 2007-09-10
> and use norton partition magic to partition

Do NOT use norton partition magic to partition.   It often does not work well with GNU/Linux.  

Use [GParted]("http://gparted.sourceforge.net") instead.  It is no cost and GPLed.

---

### Post by Tiger-Smith on 2007-09-10
And make sure you defrag your harddrive in Windows as it likes to store files all over the harddrive sectors, otherwords you might come back to losing some files.

---

