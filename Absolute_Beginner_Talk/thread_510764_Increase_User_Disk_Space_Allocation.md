---
title: "Increase User Disk Space Allocation"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ixman on 2007-07-26
As I am new to Ubuntu from XP, I dual-booted it on my laptop.  So far, I love the way it works, and look forward to a life free from Vi$ta.

Now, my installation was a 15 G installation.  I notice that when I hit Places, then, and then hit "Properties" on my user name, I only have 1.5 g allocated to me.  This has put a crimp on putting music files into my user name's space.

I tried to run gparted, but all of the menus are greyed out.

My goal is to increase the user allocation to the 40+ G I have available per the disk manager.  If possible, I'd like to eliminate the WinXP partition to boot (pardon the pun!).

I have a feeling this is something really easy and beginner-y, but I've no clue.  Are there any wise solons out there who can assist?

Thanks in advance for the help!

ixman

---

### Post by jfinkels on 2007-07-26
> **ixman said:**
> As I am new to Ubuntu from XP, I dual-booted it on my laptop.  So far, I love the way it works, and look forward to a life free from Vi$ta.

Now, my installation was a 15 G installation.  I notice that when I hit Places, then, and then hit "Properties" on my user name, I only have 1.5 g allocated to me.  This has put a crimp on putting music files into my user name's space.
 I don't really understand where you found this information, but you can view your partitions and sizes by opening the terminal ("Applcations > Accessories > Terminal") and typing the following:```
sudo fdisk -l
``` (that's a lowercase L) and type your password when prompted.
> 
I tried to run gparted, but all of the menus are greyed out.

Open a terminal as before, OR press <Alt>+<F2> to open the "Run Application..." dialog, then type the following:```
gksudo gparted
``` and type your password when prompted.

You need to have root user access to run programs that allow you to edit system files (or disks/partitions). Click the links in my signature for lots of good beginner's information.

---

### Post by davidjmayo on 2007-07-27
You cannot use Gparted on mounted partitions/disks which is why they are greyed out.

You can do what you want 2 ways
1 use your Live CD and run Gparted from it so your partitions aren't mounted

2 The better way. Use the Gparted Live CD. It's a more recent version and only 49MB so loads much qicker
download it from here and burn to CD
 [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by vanadium on 2007-07-27
I am surprised that after installing on 15 GByte, you would only have 1.5 MBytes left. The system  itself should not take more than 3 - 4 G, so that should leave about 10 G left for personal data. Perhaps you created a separate home partition? Then, of course, there will be free space left in the root partition, and the space available under /home is then limited by the size of the /home partition.

If I were you, I first try other options for putting large amounts of data like music files. You could put the music on free space in your Windows partition and then create a symbolic link to that data under your home directory. This way, your music will be available to you in just the same way (from a users perspective) as if it were residing on the home partition.

Alternatively, buy an external USB hard drive. They are very cheap nowadays.

If you really want to fix partitions etc. differently, it is all possible, but requires some knowledge and skill. Don't tempt that before you have safely backed up your user data.

---

