---
title: "Trying to install Debian Having trouble"
date: 2012-08-03
forum: Any Other OS
---

### Post by UltimateCat on 2012-08-03
This is my second try at installing Debian with the cd/dvd that I burned.
I'm in a dual boot with Windows XP and I am trying to swap with Ubuntu.
So far this is where I get during the install than I run into a problem.

1. In the partition Mgr I deleted every partition except the Windows stuff.
2. I make a new partition for the Debian install and include the / for the mount and that goes well. 

But when I make the next new partition for the swap space (1GB) and click continue it shows me: ext journal filesystem &
                                   /home
The word swap does not appear anywhere on that page to highlight it.
And, it turns the 1 GB partition that I made for the swap into 999.9 GB when I go back one click to correct the size-:(

Any ideas?   I'm not sure what is going on here.

Should I have made the swap first?

---

### Post by UltimateCat on 2012-08-03
I was following the member's instructions that he/she advised  me in this thread when this went wrong.
ubuntuforums.org/showthread.php?t=2035594

Can installing a  distro be complicated sometimes?

Please; advise

---

### Post by drawkcab on 2012-08-04
might be easier to set up your paritions using gparted first and then run the installer

---

### Post by UltimateCat on 2012-08-04
The G-parted program that I have is installed within my Ubuntu OS.
I will have to open the program and learn more as I have not used it.

If I use this G-parted will it cause my Ubuntu to crash?
(when I delete partitions and create new ones)

Could you sent me a link or webpage to help me to learn how to use Gparted?

---

### Post by Fwission on 2012-08-04
What I did is created the free space by deleting the partitions I did not want (make sure you delete not just wipe data). Then I clicked the free space and did an automatic partition. Debian will then ask you how to break down the free space (I believe swap is mandatory)

---

### Post by UltimateCat on 2012-08-05
> **Fwission said:**
> What I did is created the free space by deleting the partitions I did not want (make sure you delete not just wipe data). Then I clicked the free space and did an automatic partition. Debian will then ask you how to break down the free space (I believe swap is mandatory)

That makes perfect sense.  Thank You Fwission; I will do just that.
Than the install should be successful.
But I'll post back after doing as you said.

---

### Post by UltimateCat on 2012-08-06
I looked at the 146 GB filesystem; it has 25 items and 77.6 GB free space.
It's boot error logs, Python 26 files, program files etc...
I think it's a recovery partition for an older version of the kernel I had 2 years ago.
When I looked in Disk Utility I didn't see that it was in my extended partition so I can't resize it.  Should I delete this partition before installing Debian?

---

### Post by Mr.Plex on 2012-08-07
Use a Ubuntu Live CD you probably have and format your computer using the GParted tool. It really is *the* defacto standard for formatting these days. Hell there is even a "Parted Magic" livecd you can use if you don't have the ubuntu disc which is superb, i recently recieved the Parted Magic disc with Linux (pro/developer) magazine recently and it was the best thing since sliced bread ill tell you what.

---

### Post by UltimateCat on 2012-08-13
> **Mr.Plex said:**
> Use a Ubuntu Live CD you probably have and format your computer using the GParted tool. It really is *the* defacto standard for formatting these days. Hell there is even a "Parted Magic" livecd you can use if you don't have the ubuntu disc which is superb, i recently recieved the Parted Magic disc with Linux (pro/developer) magazine recently and it was the best thing since sliced bread ill tell you what.
I was able to successfully install Debian 6.0.5 in a dual boot with Windows!

---

