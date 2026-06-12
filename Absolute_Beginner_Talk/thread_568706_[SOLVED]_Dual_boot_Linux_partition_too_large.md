---
title: "[SOLVED] Dual boot Linux partition too large"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-06
Here's the situation: I have a Windows XP computer that has a very large hard drive, maybe 300 gig. About 95 of it was taken up with the Windows partition. I wanted a dual boot computer

I finally installed  Ubuntu Feisty 7.04 after several attempts, and I got my dual boot. However, when I was moving the slider in step 4, I got stuff exactly backwards. I wanted a 20-gig space dedicated to Ubuntu and the rest, around 280, dedicated to Windows. So I slid the slider as far to the right as possible, and it got to about 95. Now instead of a small Ubuntu partition and a huge Windows partition, I have the opposite, and my Windows is almost unusable because of it.

I did try to do something with the gnome partition manager, but it would not shrink, said something about errors in the disk. Meanwhile, I have Grubb come up at boot time.

So, now what do I do besides reformat and reinstall Windows and Linux?

Regards,

Alan

---

### Post by overdrank on 2007-10-06
> **Alan Stancliff said:**
> Here's the situation: I have a Windows XP computer that has a very large hard drive, maybe 300 gig. About 95 of it was taken up with the Windows partition. I wanted a dual boot computer

I finally installed  Ubuntu Feisty 7.04 after several attempts, and I got my dual boot. However, when I was moving the slider in step 4, I got stuff exactly backwards. I wanted a 20-gig space dedicated to Ubuntu and the rest, around 280, dedicated to Windows. So I slid the slider as far to the right as possible, and it got to about 95. Now instead of a small Ubuntu partition and a huge Windows partition, I have the opposite, and my Windows is almost unusable because of it.

I did try to do something with the gnome partition manager, but it would not shrink, said something about errors in the disk. Meanwhile, I have Grubb come up at boot time.

So, now what do I do besides reformat and reinstall Windows and Linux?

Regards,

Alan

HI, you can use the live cd to resize your partitions. Boot  the live cd and under system, administration gparted. Gparted will allow you to resize the partitions because the drive will not be mounted. You do need to defrag windows a couple of times before attempting this and BACKUP your data. Good luck!

---

### Post by Alan Stancliff on 2007-10-06
> **overdrank said:**
> HI, you can use the live cd to resize your partitions. Boot  the live cd and under system, administration gparted. Gparted will allow you to resize the partitions because the drive will not be mounted. You do need to defrag windows a couple of times before attempting this and BACKUP your data. Good luck!
Hi Overdrank,

Fortunately, I did back up my C Windows drive before beginning my adventure. The problem I am having with that partition manager is this: It will let me resize dev/hda2 (ext3) but it won't let me move it so that I can expand my C drive, using my Windows utility. 

So here's what I want to do:
[LIST=1]
[*]Resize the partition to something much smaller. It will only allow me to create space at the end. Creating space at the beginning option is grayed out
[*]Move the partition so that my empty space is between the C Windows and the first Ubuntu partition
[*]I can then boot to Windows and  use my Windows utility (Acronis Disk Manager) expand my Windows C drive to a workable size
[/LIST]

If you would like, you can check out [COLOR="Blue"]**_[this previous thread]("http://ubuntuforums.org/showthread.php?t=566993&highlight=stancliff")_**[/COLOR], where I described the problems I was having in the first place.

---

### Post by kirios on 2007-10-07
[COLOR="DarkRed"]An easy (but crude) way: 

Boot from the Ubuntu live CD. 
Open a terminal (from the Accessories menu) and type the following line: 
```
sudo swapoff -a
```
Start up the hard disk install, select 'custom' or 'manual' partitioning in Step 4, delete the Ubuntu partition(s), then resize the Windows partition, and create a new partition for Ubuntu (formatted as ext3) and a new swap partition. [/COLOR]

---

### Post by bodhi.zazen on 2007-10-07
> **Alan Stancliff said:**
> Hi Overdrank,

Fortunately, I did back up my C Windows drive before beginning my adventure. The problem I am having with that partition manager is this: It will let me resize dev/hda2 (ext3) but it won't let me move it so that I can expand my C drive, using my Windows utility. 

So here's what I want to do:
[LIST=1]
[*]Resize the partition to something much smaller. It will only allow me to create space at the end. Creating space at the beginning option is grayed out
[*]Move the partition so that my empty space is between the C Windows and the first Ubuntu partition
[*]I can then boot to Windows and  use my Windows utility (Acronis Disk Manager) expand my Windows C drive to a workable size
[/LIST]

If you would like, you can check out [COLOR="Blue"]**_[this previous thread]("http://ubuntuforums.org/showthread.php?t=566993&highlight=stancliff")_**[/COLOR], where I described the problems I was having in the first place.

Yea, most of these types of problems are solved by using a newer version of gparted. 

You can either download gusty or gparted live

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Alan Stancliff on 2007-10-07
So I'm assuming that if I boot from a CD, wipe out the Ubuntu, resize my Windows drive, and reinstall Linux to a partition with a more workable size, the Grubb won't get confused? I won't have to do anything with that?

Regards,

Alan

---

### Post by bodhi.zazen on 2007-10-07
> **Alan Stancliff said:**
> So I'm assuming that if I boot from a CD, wipe out the Ubuntu, resize my Windows drive, and reinstall Linux to a partition with a more workable size, the Grubb won't get confused? I won't have to do anything with that?

Regards,

Alan

First, you should not need to do anything that drastic. Try a newer version of gparted first.

Second, yes, it is best to manage your partitions from a live CD

Third, well if you delete the Ubuntu partition you will not be able to boot windows without restoring the windows boot or re-installing Ubuntu.

If you re-install Ubuntu, all should go well ...

---

### Post by Alan Stancliff on 2007-10-07
> **bodhi.zazen said:**
> First, you should not need to do anything that drastic. Try a newer version of gparted first.

Second, yes, it is best to manage your partitions from a live CD

Third, well if you delete the Ubuntu partition you will not be able to boot windows without restoring the windows boot or re-installing Ubuntu.

If you re-install Ubuntu, all should go well ...
Well, I hope this is not some giant balls-up. I got my Acronis rescue disk with Disk Director, and right now as I write this, it is busily deleting Ubuntu and then resizing the C partition to full. I don't know if that will make my system unbootable, but I suspect so. It has another hour or so to go.

Then I'll boot with the Ubuntu live CD and reinstall. 

The reason I did not go with the Gparted is this:

I figured I'd best reinstall Ubuntu. It was a fresh install, so nothing is really lost. If I use GParted, then I would be resizing the Windows partition with it. I'm not completely confident it can handle NTFS without breaking it. So I figured I'd just use the Acronis, which can handle NTFS, by all reports.

I sure hope this works. Otherwise I'll have to reformat the hard drive and recover my backup of my system (Acronis True Image) which I just did a short time ago.

Please let me know what you think. 

Regards,

Alan

---

### Post by Alan Stancliff on 2007-10-07
> **Alan Stancliff said:**
> Well, I hope this is not some giant balls-up. I got my Acronis rescue disk with Disk Director, and right now as I write this, it is busily deleting Ubuntu and then resizing the C partition to full. I don't know if that will make my system unbootable, but I suspect so. It has another hour or so to go.

Then I'll boot with the Ubuntu live CD and reinstall. 
***************SNIP***************
**[SIZE="3"][COLOR="RoyalBlue"]UPDATE[/COLOR][/SIZE]**

It worked wonderfully! I'm up and going now. Now I just have to figure out this operating system. As they say, one step at a time.

So thanks to Overdrank, Kirios, and Bodhi.Zazen for all the help.
:lolflag:

---

### Post by kirios on 2007-10-07
> **Alan Stancliff said:**
> It worked wonderfully! I'm up and going now. Now I just have to figure out this operating system. As they say, one step at a time. 
[https://help.ubuntu.com/6.06/book/book-toc.html]("https://help.ubuntu.com/6.06/book/book-toc.html")

---

