---
title: "How should I partition my HDD??"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-07
When I installed Feisty Fawn from the LiveCD I let it choose how to make my partitions.

Since then I have realised I should have done this manually and create additional partitions for storage and an area to backup my OS.

[img]http://i16.tinypic.com/4pezev6.jpg[/img]

So I would like to start all over again and manually do this.

What suggestions/advice would you give me ?

BTW I'm only going to make the SWAP file 1GB as it's hardly being used by any applications I'm using.

Thanks :)

---

### Post by bone2006 on 2007-09-07
put home on a separate partition ,size is up to u

---

### Post by yabbadabbadont on 2007-09-07
With that size drive, I would make the root partition 8 or 12 gig.  That should be a lot more than you would ever need.  1 gig for swap as you indicated, and all the rest for a separate /home partition.  That way you can wipe and reinstall if needed without too much trouble.  (I just backup the /etc directory when I reinstall)

Edit: Too slow.  :D

---

### Post by chrome307 on 2007-09-07
Thanks for that :)

Would it be advisable to create a partition (?) where I could clone my ROOT, so if I needed to reinstall I could simply copy over the contents to the ROOT partition again .... does that make sense?

---

### Post by bone2006 on 2007-09-08
I'm sure others have more experience than I do, but if your putting your home on a separate partition and then your putting root on the another partition, why not just back a complete backup?  The home has your desktop and all your settings, so say you want to format the root and reinstall ubuntu, it makes makes it really easy.  

I believe the majority of people who have been using linux for awhile have home on another partition, but not the root.

---

### Post by crazybilly on 2007-09-08
for what it's worth, on my dual-boot machine, my linux partition is 7.7 gb.  and it's too small.  

If I was smart/not lazy, I'd set up my windows data partition as my root directory, but I'm going to have to learn how to ln properly first. 

That'd save me some space, but I'd still do at least 10 gb for your root parition.

---

### Post by ORBiTrus on 2007-09-08
My laptop(s) is:
OS X: 13GB
XP: 9GB
Ubuntu: 6GB
Arch: 5GB
FreeBSD: 7GB
Solaris: 8GB

That's all for Data and settings.  Documents are stored on the remaining space using a messy symlink + rsync system to keep my Desktop / Workstation / Laptop A / Laptop B / Server with the same data.

For a well-written guide to Linux partitioning, I recommend the Gentoo Handbook, Disk Partitioning section.

---

### Post by chrome307 on 2007-09-08
This is all very confusing to me haven't read this article:

[http://www.pcmech.com/article/installing-ubuntu-linux/](http://www.pcmech.com/article/installing-ubuntu-linux/)

==============================================

You should see your primary hard drive (hda) which has your Windows installation with all of its partitions listed. We are going to leave this one alone. Additionally, you will see your empty hard drive (hdb, hdc, or hdd) with the size of the drive listed followed by &#8220;FREE SPACE&#8221;.

Highlight &#8220;FREE SPACE&#8221;, press enter and then select the option to create partition. [COLOR="Red"]**We are going to first create the &#8220;/&#8221; partition which is equivalent to the Windows C drive. All of your programs and libraries (libraries in Linux are similar to Windows DLL&#8217;s) will be stored on this &#8220;/&#8221; partition[/COLOR].** ....

After entering the size, select Primary as the partition type. Next you will be asked where to place the partition on the disk. Since &#8220;/&#8221; is our workhorse partition which will store all our crucial Linux operating system files, including the information we need to boot the system, it makes sense to place it at the beginning. At last you will be presented with a partition configuration screen. You will see the option to change the partition file system, but lets leave it with the Linux standard, ext3.

You should now notice some of the free space has been allocated to your &#8220;/&#8221; partition. We still have a couple of more partitions to set up so highlight &#8220;FREE SPACE&#8221; again and create our swap partition. The swap partition is used for temporary random storage in case your computer doesn&#8217;t have enough memory to store what programs demand. Additionally, if you hibernate your computer, all the contents of your memory are stored in the swap. Windows refers to this as &#8220;virtual memory&#8221;. Make this a primary partition and place it at the end of your drive. At the configuration screen, change the partition to a swap area. Apply the changes.

[COLOR="Red"]**Lets set up the final partition. Select the remaining &#8220;FREE SPACE&#8221; and assign all of your remaining space to this primary partition. When you get to the configuration screen, notice the mount point is set to &#8220;/home&#8221;. The /home directory in Linux is equivalent to &#8220;My Documents&#8221; in Windows. **[/COLOR]

For example the user I am going to set up, &#8220;jason&#8221;, has its own directory (/home/jason) which stores all my personal settings and files. The reason we make this a separate partition is for abstraction. For example, we can format our &#8220;/&#8221; partition for a new install or distribution upgrade without losing any data&#8230; even better, all my settings such as bookmarks and playlists will be kept no matter what happens to the &#8220;/&#8221; partition. Pretty neat idea. Apply your changes, this is the last partition!


===========================================================

Is this not the case with Ubuntu ???

---

