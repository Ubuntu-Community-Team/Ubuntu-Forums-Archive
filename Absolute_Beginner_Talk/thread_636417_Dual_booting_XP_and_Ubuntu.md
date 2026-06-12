---
title: "Dual booting XP and Ubuntu"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-12-09
I have XP installed on my laptop and want to dual boot Ubuntu with it, I already have Gutsy on Live CD, I was wondering, how do I dual boot the 2 OS's?

---

### Post by alsamman on 2007-12-09
go to System>Preferences>GParted
make a ext3 partition as well as a swap partition
the ext3 will be your linux hardrive so make it as big as u like
the swap partition should be around twice as much as ur RAM
run the installation and then when it asks how you want to parition, select Manual
in there edit your ext3 parition and remove the media/..... to just '/' (without apostraphes)
then click the button to format
click next and its quite simple from there

---

### Post by hotweiss on 2007-12-09
Ubuntu will automatically configure the boot manager for you, actually there's nothing to worry about.

---

### Post by RobotoWorks on 2007-12-09
Im sorry I think you guys misunderstood me, I have XP on my laptop, I downloaded Ubuntu Gutsy ISO and put it on Live CD, I want to dual boot Ubuntu with my pre installed XP, how do I do that?

---

### Post by alsamman on 2007-12-09
put in the livecd and restart your computer, you will be prompted with a screen that says something like 
start or install ubuntu
start in safe graphics
blah blah blah

press enter on Start or install ubuntu and then itll take you to the ubuntu desktop and from thereon, follow instructions stated previously

---

### Post by RobotoWorks on 2007-12-09
For some reason that doesnt seem too right, anyone else, is that the correct way?

---

### Post by Joeb454 on 2007-12-09
yep.

Back-up anything you want to keep on your XP system (just in case)

Also make sure you click System > Administration > Partition Editor before you install anything though.

And then select the XP partition (it'll be the big NTFS one I assume) and shrink it, then after that's finished, double click install and follow the instructions

---

### Post by RobotoWorks on 2007-12-09
What size to I shrink it to?

---

### Post by Joeb454 on 2007-12-09
I shrunk my Vista partition by 15gb so my Ubuntu partition has 15Gb of space to use (though I saved space by keeping all my music on the Vista partition :))

WIth Gutsy it seems to take *a lot* longer than Fiesty, although I will admit it does seem to do more

---

### Post by RobotoWorks on 2007-12-09
This is still a bit confusing for me, can anyone link me to a good tutorial?

---

### Post by overdrank on 2007-12-09
> **RobotoWorks said:**
> This is still a bit confusing for me, can anyone link me to a good tutorial?

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by RobotoWorks on 2007-12-09
Thanx :)

---

### Post by RobotoWorks on 2007-12-09
Okay, Im on the Ubuntu Live CD right now, Im at the part where I need to choose either, tolpartition the drive or use the whole drive
[http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)

I assume I must click the first option, what size should I make that first option?

---

### Post by spiderbatdad on 2007-12-09
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=0&value=dual+boot+installation+Gutsy&context=160](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=0&value=dual+boot+installation+Gutsy&context=160)

---

### Post by RobotoWorks on 2007-12-09
Im sorry that doesnt help any, as Im trying to dual boot with XP, not Vista, can anyone whose done this before, help me out?

---

### Post by spiderbatdad on 2007-12-09
There should have been numerous links on that page, not just one pertaining to Vista. Perhaps I sent a bad link. Anyway, as has already been pointed out, you put the cd in and after you're logged in, you install it. Couldn't be much simpler. There are numerous tutorials and several appear in this thread. I believe it is suggested to defrag your windows installation just prior to installing. I'm not sure you understand the term Dual-boot. You will still only be running 1 OS at a time.

---

### Post by RobotoWorks on 2007-12-09
I know I can only run 1 OS at a time, but I want to dual boot Gutsy and XP so I can choose which run I want to run at which time, my question again is, how do I partition the drives so I dont end up over righting Windows XP with Ubuntu.

---

### Post by bren on 2007-12-09
use the whole drive will wipe your xp so you don't want to do that.......

you want to select the option that will shrink your xp parition a bit but still leave room for expansion..... and then dedicate the rest to linux.

you can do this via the slider in the "auto" partition screen

or you can click manual and choose the sizes yourself....

hard to give you exact advice without knowledge of your system

(how many hard disks, how much used etc)

if you post the screenshot (Applications->Accessories->Take Screenshot) here then you will get more exact advice

hope that helps

bren


by the way if you havent' backed up xp and defragged xp at least twice then stop install and do that first

---

### Post by RobotoWorks on 2007-12-09
> **bren said:**
> use the whole drive will wipe your xp so you don't want to do that.......

you want to select the option that will shrink your xp parition a bit but still leave room for expansion..... and then dedicate the rest to linux.

you can do this via the slider in the "auto" partition screen

or you can click manual and choose the sizes yourself....

hard to give you exact advice without knowledge of your system

(how many hard disks, how much used etc)

if you post the screenshot (Applications->Accessories->Take Screenshot) here then you will get more exact advice


bren


by the way if you havent' backed up xp and defragged xp at least twice then stop install and do that first




When I click the first option, it starts to partition. a few seconds afterwards, an error message popsup stating "And error has occurred while writing the changes to the storage device, the resize operation is aborted"
hope that helps

---

### Post by Sef on 2007-12-09
1) Did you defrag XP at least twice before starting the install?

2) Did you md5sum the download?  (To make sure it is good.)

3) Did you burn the iso at 4x or less?  (Faster can corrupt the download.)

4) Did you check the disk for errors?  (Instead of going into the Live CD, go down the list, check disk or something similar.)

---

### Post by RobotoWorks on 2007-12-09
I did all but the first one, how do I defrag XP?

---

### Post by Sef on 2007-12-09
If my memory serves me correct, defrag is under

Programs > System Tools > defrag

---

### Post by RobotoWorks on 2007-12-09
Thanx, Im defragging it now, I just wiped my hard drive about 2 hours ago, do I still need to derfg it?

---

### Post by Dr Small on 2007-12-09
Um, if you wiped your hard drive, how are you defragging it ?

---

### Post by RobotoWorks on 2007-12-09
Well I used my recovery disk to wipe my hard drive to when it came right out of the factory. I am  in Win XP, and Im using the defragment tool.

---

### Post by RobotoWorks on 2007-12-09
So I just got the defragment done, I checked the CD and there are no corrupt files, and it loads just fine. Now for my question, how to I partition the drive in such away so I can dual boot Win XP and Ubuntu?

---

### Post by Dr Small on 2007-12-09
> **RobotoWorks said:**
> So I just got the defragment done, I checked the CD and there are no corrupt files, and it loads just fine. Now for my question, how to I partition the drive in such away so I can dual boot Win XP and Ubuntu?
Go back to the psycocat's link and read. it is very easy, and I have done it that way:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by RobotoWorks on 2007-12-09
I did follow the tutorial it was easy enough, but back a few pages, I explain of an error I get.

---

### Post by baxterdog on 2007-12-09
First, with windows, it's best to do a disk cleanup before defragging. Then do it again. Simply put the Ubuntu disk in and follow the directions. (Not to sound like a jerk)

Also with Xp to do a disk check; you have to right-click MyComputer and choose tasks-->disk check (not sure if this is the right terminology as I am not on a windows machine). It will then popup with some stupid square asking if you want to do this and then tell you that it will then have to be done after the next reboot stupid popup.

---

### Post by RobotoWorks on 2007-12-09
When I try to setup the partitions automatically, I get an error, so I have to do it manually, can someone help me with this?

---

### Post by RobotoWorks on 2007-12-09
Anyone?

---

### Post by thelatinist on 2007-12-09
Download the GParted Live CD from [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) and resize using that.  Then run the tutorial, choose manual, and choose to install in the largest free space.

---

### Post by RobotoWorks on 2007-12-10
I recently changed to Vista, so now I want to boot Ubuntu on Vista.

---

### Post by Ex-windows on 2007-12-10
I am a noob and was able to do this so it is quite easy. here are some links for dual boot info. I hope this helps

Dual boot page
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Official Ubuntu site
[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)
[https://help.ubuntu.com/7.04/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/7.04/installation-guide/i386/non-debian-partitioning.html)

---

### Post by dptxp on 2007-12-10
It does not matter if you want to dual boot with XP or Vista. You need to resize the Windows partition to make partitions for Ubuntu, at least 2, one / and other SWAP.
When you install Ubuntu (with Windows on C drive) in the / partition, you will be able to select your OS from GRUB menu after booting the machine.
You can resize, make and format partitions while installing Ubuntu in step 5, you can choose manual mode.

Rule is have Windows first on C drive, then install Ubuntu.

---

### Post by meindian523 on 2007-12-10
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

Hopefully,this settles all your questions?

---

