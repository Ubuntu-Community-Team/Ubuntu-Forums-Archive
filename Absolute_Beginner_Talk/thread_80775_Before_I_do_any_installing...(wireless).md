---
title: "Before I do any installing...(wireless)"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by rcarey on 2005-10-22
Hi there.

I'm very interested in converting my Windows Laptop into a Linux Laptop.  I've already used the "boot" CD, and would really like to go through with this.

Anyway, before I go ahead and do anything, I would like to inquire about the wireless situation.  I've heard that it's difficult to get your wireless connection on the laptop working under Ubuntu.  How hard is it?  And are there any specific qualifications I should know about ahead of time?

I guess what I'd like to know is if there is any way to tell ahead of time whether my wireless connection will be messed up or not.

Also, if it does end up getting screwed up, is there an easy way of going back to my old Windows settings?

Thanks for your help.

---

### Post by x96riley3 on 2005-10-23
There are tons of pages here on wireless.  If you type wireless in the forum search you will find tons of info.  That said...

I bought a brand new laptop from Dell 5 days ago and I installed ubuntu on it without knowing anything about ubuntu.  I have the pentium M processor.  I didn't know anything about my wireless laptop or ubuntu but I spent time searching these forums for answers and I found them.  

Most people get there hardware working.  Check the forums for someone with your hardware and see if they got it working.

What I did:

I went to the Dell website and downloaded the windows wireless driver.  Yes I did say the windows driver.  I saved it on my Linux laptop. The driver was the typical windows exe file.  All I did was unzip the exe file so that I could get the inf file(unzip  drivername).  

I ran the following command as root:

**1.  /usr/sbin/ndiswrapper -i bcmwl5.inf**

_What is ndiswrapper?_

ndiswrapper  -  Linux kernel module and user space tool to load and run
       Windows XP drivers for wireless cards

**2. modprobe ndiswrapper**

_What is modprobe?_

 modprobe - program to add and remove modules from the Linux Kernel

**3. iwconfig**

You should see a wlan0.  

**4. iwlist wlan0 scanning**i

This will show you all the hostspots available.  You can download and install a program called wifi-radar that will show you hotspots or your own router.  It lets you connect to those hotspots.

Good Luck

-X

---

