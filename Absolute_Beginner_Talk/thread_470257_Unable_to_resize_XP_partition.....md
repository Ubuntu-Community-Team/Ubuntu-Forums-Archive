---
title: "Unable to resize XP partition...."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by josel777 on 2007-06-10
For the the past couple of days I have been trying to install Ubuntu 7.04 (64 bit) on my new Compaq V6110US laptop. Here are my laptop specs:
AMD Turion 64x2 TL-50 1.6GHz
100G Hard disk
512 Memory DDR2-667 
nVidia GeForce GO 6150 video card

At first I was using the regular installation CD. But it didn't work at all. I encountered the same issues described in this tread:
[http://ubuntuforums.org/showthread.php?t=456125](http://ubuntuforums.org/showthread.php?t=456125)

I then tried using the alternative installation disc. For some reason I am unable to resize the XP partition. I am getting the following message:
----------------------------------------------------------------------------------------------
The resize operation is impossible
Because of an unknown reason it is impossible to resize this partition.
Check /var/log/syslog or see virtual console 4 for details.
---------------------------------------------------------------------------------------------------

I have tried using partition magic but will not recognize any partition letters. 
I have also tried using Gparted without success.

Any help is most appreciated.

---

### Post by mikewhatever on 2007-06-10
A chkdsk check might help, and if not, try disabling the page file in XP.

---

### Post by bren on 2007-06-10
I havent had your specific problem but some things could be affecting this

a) you need to defrag twice in windows
b) maybe you could use xp to re-partition first then try ubuntu install again?

---

### Post by Skidpad on 2007-06-10
Here are a couple of threads I posted in regarding installation on an XP laptop (mine included).  It's probably your hibernation file - XP won't let Ubuntu move it for installation...but you can - read these links:

[Link #1]("http://ubuntuforums.org/showthread.php?t=378825")

[Link #2]("http://ubuntuforums.org/showthread.php?t=366409")

---

### Post by josel777 on 2007-06-11
Thanks for all your input. Unfortunately I am still unable to resize my XP partition. 

I disabled page and hibernation files and defragmented the harddrive several times. I rebooted and tried resizing the XP partition using the Alternate CD. It is still not working. I keep getting the same message:

----------------------------------------------------------------------------------------------
The resize operation is impossible
Because of an unknown reason it is impossible to resize this partition.
Check /var/log/syslog or see virtual console 4 for details.
---------------------------------------------------------------------------------------------------

Any other ideas?

---

### Post by josel777 on 2007-06-11
I am thinking about reinstalling XP from scratch and setting my partition size then. 

However, I still don't get why I am unable to resize my current partition.

---

### Post by TriggerHappyChewie on 2007-06-11
Use the Gparted LiveCD, that always works.

[http://gparted.sf.net](http://gparted.sf.net)

---

### Post by josel777 on 2007-06-11
I have tried using the Gparted Live CD severals times. Below are the last 2 lines I get:


PCI: Probing PCI Hardware
0000:00:0d.0: cannot adjust bar0 (not I/O)

---

### Post by ugm6hr on 2007-06-12
> **josel777 said:**
> I have tried using partition magic but will not recognize any partition letters. 
I have also tried using Gparted without success.

If Partition Magic does not recognise your partitions - there is presumably some partition tabel error (although Partition Magic normally overcomes this).  Does your HD work OK?  Can you access all the partitions in Windows?  Might be worth running a diagnostic on the HD to check for errors on the drive (find it in your HD manufacturers website, or try [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Also - might be worth posting a screenshot of PartitionMagic / GParted to see what your setup looks like.  Sorry if you're a much more advanced user than I am assuming.

---

### Post by Skidpad on 2007-06-12
> **josel777 said:**
> I have tried using the Gparted Live CD severals times. Below are the last 2 lines I get:


PCI: Probing PCI Hardware
0000:00:0d.0: cannot adjust bar0 (not I/O)
This leads me to believe it may be an errant hardware issue (?).  I don't know if reinstalling XP would fix this, but  I will admit to being out of my element here, sorry I can't be of more help.

Any updates?

---

### Post by josel777 on 2007-06-13
I am still unable to resize the XP partition. I plan on wiping everything off tomorrow so that I can start from scratch. I have never had this issue before. I have installed Red Hat and Fedora on several other computers without any issues. For some reason my laptop is being VERY difficult.
I will provide an update tomorrow night. Wish me luck.

---

### Post by josel777 on 2007-06-13
So I reinstalled XP and was finally able to install Ubuntu 7.04. However, I am still having issues.
For some reason Ubuntu is having a hard time booting. I am unable to get the GUI. 
I am getting the following error code:

bcm43xx: errror: microcode "bcm43xx_microcode5.fw" not available or load failed

What can I do?

---

### Post by Skidpad on 2007-06-14
^^^^  The "bcm43xx" is an indication for a Broadcom wireless card; the driver isn't loading properly?

---

