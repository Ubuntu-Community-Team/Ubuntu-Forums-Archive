---
title: "[SOLVED] Installing Feisty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-19
Guys is just bought a new computer. Its been shipped but i havent received it yet. However I thought i should get a head start in knowing what I need to, well in advance.
 
Anyway the config is :
 
[FONT=Arial][SIZE=2]- Genuine Windows Vista Home Premium (32-bit) :roll:[/SIZE][/FONT]
[SIZE=2][FONT=Arial]- Intel(R) Core(TM) 2 Duo T5200(1.60GHz/2MB L2Cache)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 17.0" WXGA+ BrightView Widescreen (1440x900)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 256MB NVIDIA(R) GeForce(R) Go 7600[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- HP Imprint Finish/Microphone/Webcam [/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 2GB (2 Dimm) RAM[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 160GB 5400RPM (80 + 80) Dual Hard Drive[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- LightScribe DVD+/-RW w/Double Layer[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth[/FONT][/SIZE]
 
I also have:
- 500 GB Western Digital External Hard Drive 7200 RPM
 
I have a few questions:
 
1) Since I have a dual hard drive, would it be a better idea to install all the OS'es (Ubuntu, Windows, Kubuntu) on the same hard drive and have shared data on the other one, or install Windows on one and Ubuntu on the other?
 
2) Speaking of Kubuntu, is it better to have a triple boot of U, K and W or should i install Ubuntu and Windows and have Ubuntu use the K-Desktop ?
--Note: I would also use the Gnome since this is my first foray into Linux...I want to try out both
 
3) How much swap memory should I have? Since I have 2GB of RAM would I really need RAMx2 = 4 GB(total) swap ? Or would this is be a waste of disk space? 
I plan to have swap on both the internal HDD's so I shall put half the swap on one and the other half on the other drive
 
4) The partition that I plan to do is
C: - 15 GB - Windows (NTFS)
D: - 10 GB - Data for Windows (NTFS)
/: - 5 GB - Ubuntu root (EXT3)
/home: - 5 GB - Ubuntu home(EXT3)
/shared: - remaining space - data(EXT3)
 
Also I plan to make my 500 GB external drive as an EXT3 partition. I have a lot of music and movies and photos on my external drive currently. Would it better to make separate partitions for them on the external drive, - as in /movies, /music, /photos ?
Or should i keep the entire 500GB of external drive as a single partition for eg. /data?
 
Does the above partition scheme make sense. Would I need other partitions like /var, /tmp, /etc, /boot etc?
 
Comments , Suggestions ? Also suggest some better partitions sizes if i have taken too much or too little for /home and the / (root)
 
 
Thanks in Advance

---

### Post by freebird54 on 2007-04-19
Well - that's a lot of planning!  Here's one possible set of answers...

1. I would have drive 1 as OS, and drive 2 as data.  This leaves swap on a separate drive from the data your working with.

2. I would have both available as separate items.  It can be confusing to have both sets of default progs in the menus together.  Besides, having 2 installation has lots of possible benefits. a) you have a Linux to start with if you need to fix something in the other one  b) you can test something in 1 before deciding if it makes into your regular setup.  c) When you decide to dump one of Gnome or KDE, you can do it easily.  d) if you want - you can run a bleeding edge system on 1 (test Gutsy perhaps) without risking your working setup.

3.  a 1 Gb swap should be plenty.  You will be unlikely to hit it at all!

4.  Room to leave.  More like this

C: NTFS - 20  (it objects during setup with less)
D: NTFS - 30  (give yourself some room in case you end up using it a fair bit

**NOTE CAREFULLY - set up and resize Vista partitions with Vista ONLY - before doing anything with other tools.  NTFS has changed again!**

swap - 1 Gb

create Extended partition at this point then:
U / - 5 should be plenty
K / - 5 shoud be plenty
/home U - 10
/home K - 10

/data  ext3 rest of space

other drive as you see fit.  Probably ext3 - as Windows can have a driver added to read/write ext3 partitions relaiably.

I would split it into a couple - so as to leave a place to put backups (including the OS's too in case of... :) )

Hope this helps!

---

### Post by LaRoza on 2007-04-19
How you partition your drives is up to you. There are many recommendations on the forums and you might want to visit those for "best practices".

You can use many desktop with Ubuntu. You just install them and you choose which one you want to use at start up.

You are getting Vista Home Premium. If you have no need for it, you can overwrite it (like me).

If you do want it you might find it easier to put Ubuntu on another hard drive.

If you want to share, using FAT32 will enable this, Feisty and Windows can read NTFS and EXT3. I believe you'll need to download something for Windows.

I used Knoppix to read NTFS off of a Windows Vista system so you'll probably have no trouble either.

To prepare for this impressive computer, you might want to research all of the hardware you are getting to see what, if anything you will need to download (drivers and such).

---

### Post by Inxsible on 2007-04-19
FreeBird, Would you please explain this statement further

**NOTE CAREFULLY - set up and resize Vista partitions with Vista ONLY - before doing anything with other tools. NTFS has changed again!**

Vista is an OEM on the machine, I probably will not have the Vista installation DVD with me unless i buy one(yeah right !!) or I pirate one ;-)
I was just planning to resize the partition to 20GB(C:)  and a 30GB (D:) as you suggested

Do you mean that I should first partition C: and D: in windows before putting in my ubuntu install CD ?

Also, I read somewhere that having swap on both internal HDD's can increase performance. So would it be better to have 512MB on each drive. Why do you think I should keep my data away from swap ?

---

### Post by freebird54 on 2007-04-19
From within Vista, there are tools for resizing partitions.  If you don't want to have to reinstall Vista, use its own tools for resizing whatever it ships with.  Yes, THEN go ahead and do the rest with installer tools of Ubuntu.  As far as I know, there is no open source solution that is YET reliable for resizing the slightly changed NTFS partitions.  (I wonder why the change?  Anti-competitive measures perhaps?)

No problems from there, and interoperability should be fine - just the resize issue as far as I'm aware.

---

### Post by LaRoza on 2007-04-19
To clarify the bold statement,

Use Vista to repartition your hard disk and then install Ubuntu to that partition.

Previously, you could have let the installation process resize the partition for you, with Vista you can not do that.

Some one on this forum tried it and lost Vista.

---

### Post by silverglade00 on 2007-04-19
I have a similar machine. If it is the same webcam that I have (and it probably is) then for now Ekiga is the only software that will be able to use it AFAIK. The cam needs Video4Linux2 and most apps use Video4Linux1.  Other than that, shrink that Vista partition only from within Vista, then do everything else from the Ubuntu CD.

---

### Post by Inxsible on 2007-04-19
Thanks Freebird, LaRoza, SilverGlade
 
Boy, am I glad I asked the question when I did !
 
Or I would have lost my Vista, not that I care too much..just for some old games I already own.
 
But honestly, I am not even sure if those games will work in Vista since a lot has changed in the transition from XP to Vista
 
SilverGlade, I shall look up on the Video4Linux2 -- thanks for the heads up !!

---

### Post by dptxp on 2007-04-19
Partition with Vista for Vista Part. No need to partition other space for Ubuntu with Vista, do it with the Ubuntu installation. Just do not fiddle Vista part with Ubuntu.

Keep Ubuntu and Kubuntu separate. Else KDE desktop gets cluttered with Gnome stuff ( the opposite also should  hold true). 10 GB is not such a big deal to keep all neat.

EXT3 format shall not be read by Vista (there may be ways, but keep all straight), FAT32 formatted partitions shall be read by both. You can keep two for data, EXT3 for large files or files that Vista may not read.

---

### Post by Inxsible on 2007-04-19
> **silverglade00 said:**
> I have a similar machine. If it is the same webcam that I have (and it probably is) then for now Ekiga is the only software that will be able to use it AFAIK. The cam needs Video4Linux2 and most apps use Video4Linux1. Other than that, shrink that Vista partition only from within Vista, then do everything else from the Ubuntu CD.
 
Since you said that the webcam can be used by Ekiga, Ekiga would probably be installing a driver correct?
 
So couldnt we install 'that' driver and have our webcams work in other softwares too.
 
Anyway, I am just laying it out there, maybe I am completely wrong on it since I havent tried it yet and so can't really say anything for sure !

---

### Post by Inxsible on 2007-04-19
How about my external drive ?
 
Should I have multiple partitions on my external drive like /music, /movies, /pics etc
 
or just one big hard drive partition /data ?
 

 
Thanks

---

### Post by Inxsible on 2007-04-19
> **dptxp said:**
> Partition with Vista for Vista Part. No need to partition other space for Ubuntu with Vista, do it with the Ubuntu installation. Just do not fiddle Vista part with Ubuntu.
 
Keep Ubuntu and Kubuntu separate. Else KDE desktop gets cluttered with Gnome stuff ( the opposite also should hold true). 10 GB is not such a big deal to keep all neat.
 
EXT3 format shall not be read by Vista (there may be ways, but keep all straight), FAT32 formatted partitions shall be read by both. You can keep two for data, EXT3 for large files or files that Vista may not read.
 
Will Vista NOT read EXT3 even with FS-Drive ?

---

### Post by freebird54 on 2007-04-19
I still think that ext3 is the better bet for shared partitions.  In Windows it is faster than NTFS, and less likely to get screwed up.  Not to mention fragmentation issues.  Not to mention the relative time required for fsck to complete!  Check out the drivers here:   [http://www.fs-driver.org/](http://www.fs-driver.org/)  and here  [http://sourceforge.net/forum/forum.php?forum_id=651377](http://sourceforge.net/forum/forum.php?forum_id=651377)

Just my opinion of course :)

---

### Post by freebird54 on 2007-04-19
I would not split it up that much.  Much too hard to know ahead of time what the relative needs of each will be.  The only reason for that many splits would be storage efficiency should you use FAT32..:)

I would have more than one partition though, as I mentioned.  It is useful to have a partition to throw backup in - because of the speed of backup from HD to HD, you are more likely to do it.  Back off from there to DVD or whatever on a less frequent basis.  That way it is tough to lose everything at once!

One nice thing is to have an image of your working boot/root at a stable point.  Makes for easy recovery from things compared to a fresh (unconfigured) install.  You have all your screens, settings, themes, and updates to that point in minutes.

Have fun planning!

---

### Post by Inxsible on 2007-04-19
^^^ Makes sense !

Thanks again Freebird !

---

