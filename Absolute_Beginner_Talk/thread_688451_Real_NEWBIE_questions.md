---
title: "Real NEWBIE questions"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Greynold on 2008-02-05
Having read some of the Newbie type posts, I think I'm in the Pre-Newbie position. But I need: directions to helpful posts or documentation on the forum just to get acquainted and some tips on a current Kubuntu system on a Gateway 500S (2003) system that my son had and was actually the Ubuntu-acolyte.
Initially, I thought he had setup the system as dual-boot, either WinXP Pro or Kubuntu.  So my first question is: How to check that this was so as I attempted to change the CMOS Boot Drive to what I thought was the WinXP partition and it still came up with Kubuntu login.

My second question what is the difference between Ubuntu & Kubuntu?

Third question, what are some diagnostics I can perform with Kubuntu from Grub>... I found that by hitting ESC on startup but I couldn't make much of the commands.  Reason I ask, is son believes that Disk Drive was corrupted somehow and needing replaced but I reset several times and it always came up to the Kubuntu Login prompt.

Fourth question, is there a hidden admin account? Son doesn't seem to remember his password. I got him a laptop to replace this system a year ago...

Lastly, I don't have the system here to work on and will have to take your suggestions home with me to try out. But I do appreciate you help and time.  I always wanted to pickup enough Linux to know my way around.
thanks,
Greynold

---

### Post by hyper_ch on 2008-02-05
Initially, I thought he had setup the system as dual-boot, either WinXP Pro or Kubuntu.  So my first question is: How to check that this was so as I attempted to change the CMOS Boot Drive to what I thought was the WinXP partition and it still came up with Kubuntu login.[/QUOTE]
When you boot up, you'll see a menu that lets you boot into "normal" mode and "recovery" mode. If there is no Windows Options in that menu, then it seems it's not dual boot. If that is the case, you can still open a terminal and run this command:
```

sudo fdisk -l

```
That will list all the drives and partitions. If one is labelled "ntfs" then you at least have some hope left.

> **Greynold said:**
> My second question what is the difference between Ubuntu & Kubuntu?
They feature different default desktop environments (Ubuntu-->Gnome and Kubuntu-->KDE)  and different set of default programs. There's a huge religious war between those two. I however prefer Xfce (Xubuntu). You can test eithr one:
```

sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop

```
At the login screen you can then select a "session" into which one you want to start.

> **Greynold said:**
> Third question, what are some diagnostics I can perform with Kubuntu from Grub>... I found that by hitting ESC on startup but I couldn't make much of the commands.  Reason I ask, is son believes that Disk Drive was corrupted somehow and needing replaced but I reset several times and it always came up to the Kubuntu Login prompt.
Could you elaborte more?

> **Greynold said:**
> Fourth question, is there a hidden admin account? Son doesn't seem to remember his password. I got him a laptop to replace this system a year ago...
Not really... there is "root" account which is the system administer but it is deactivated. Normally the user setup during install has also admin rights. You use "sudo" for that or you are prompted for a password (which will be your normal user password). [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Greynold said:**
> Lastly, I don't have the system here to work on and will have to take your suggestions home with me to try out. But I do appreciate you help and time.  I always wanted to pickup enough Linux to know my way around.
No problem with that ;)

---

### Post by Nythain on 2008-02-05
1. you could open up a terminal session (not sure on how to do this or what its called in gnome but in kde you would click on the k button for the kmenu, go to system, and down to konsole) and type
```

sudo fdisk -l

```and look for any ntfs partitions, if there are, its a pretty good sign that its set up to dual.
Next, to really find out... while the computer is booting... after the bios... it should give you 3 seconds to hit ESC to bring up a grub menu... if you dont hit esc in 3 seconds (thats the default, unless he changed it) it will automatically boot to the first os in the grub menu list, wich is usually ubuntu.
After hitting esc on time, it should show you a list, Ubuntu-yadda-yadday-yadda, Safe Mode yadda yadda and hopefully a Windows XP, or windows of any fashion, option
If there's not a windows option, its a pretty good chance he didnt have it set up to dual boot.

2. Ubuntu ships with Gnome as default Desktop Environment, Kubuntu ships with KDE as default Desktop Environment... Difference between Gnome and KDE is a bit trickier and ultimate boils down to personal preference

3. Cant help ya much there
EDIT: it just occured to me that whatever "disk drive" damage that he thinks might have occured, might have somehow wiped out any info pertaining to the dual boot he might have had set up... not really sure, was just a thought

4. yes and no... the first/primary user account created usually acts as teh "admin" but there is a "root" account, not active by default, it might be teh best option for you if somone else cant help you with "resetting" the original password...

5. hopefully with ubuntu and the ubuntu forums you'll be a l33t linux guru in no time :)

---

### Post by neurostu on 2008-02-05
> How to check that this was so as I attempted to change the CMOS Boot Drive to what I thought was the WinXP partition and it still came up with Kubuntu login.

When you install Ubuntu, grub is installed by default.  Grub moves into the location on your HDD were the windows boot loader used to be. So you shouldn't edit the Boot setup in your CMOS. You just need to get GRUB to point to the windows installation.  If you search google or the forums for a way to manually configure grub you will get plenty of hits that explain this.

> 
My second question what is the difference between Ubuntu & Kubuntu?

The operating systems are the exact same; however, Kubuntu uses KDE for a GUI and Unbutu uses Gnome.

>  what are some diagnostics I can perform with Kubuntu from Grub>... I found that by hitting ESC on startup but I couldn't make much of the commands. 

I'm not sure what your asking. Does grub boot normally when you turn on your computer? Can you select to boot Ubuntu or Windows?

>   is there a hidden admin account? 

Ubuntu does have a root account (its an admin)  but you can't log into it and most people don't use it. Here is a walkthrough on how to reset passwords [http://ubuntuforums.org/archive/index.php/t-3609.html]("http://ubuntuforums.org/archive/index.php/t-3609.html")


Hope this helps

---

### Post by Greynold on 2008-02-05
Thanks guys,
You've given me some good info and when tied with other similar posts; I feel comfortable trying a few things this evening.  Based on what I vaguely recall -- I'm wondering if he eventually blew away the WinXP and overwrote with either an upgrade to Ubuntu or installed Kubuntu in one partition with Ubuntu on the other...?  
I'll know when I check the disk file structure for ntfs/FAT-32...

I still feel more comfortable right now with WinXP... Any recommendations on which should be purged should it be necessary to re-install WinXP?
Thanks,
Greynold

---

### Post by neurostu on 2008-02-05
The easiest way to get a dual-boot XP / Ubuntu system would be to install Win XP and nuke everything. Then install ubuntu using an ubuntu live CD. The only difficult part will be on the partitioning. Make sure it doesn't use the entire drive but rather uses part of it.  

To re-install ubuntu will only take about 30 minutes (Which is a lot less time then it would take you to install XP while preserving the current ubuntu installation).

Also a fresh ubuntu install will let you setup your own account and PW.

I would highly recommend this!

Have fun and good luck!

---

### Post by Greynold on 2008-02-05
Just heard from son... Once he heard system was coming up Ok! and asking for PWD -- don't think he wants me to pursue any further.

I'll still look at some of the settings you guys have replied with just to see if I can gain a little more familiarity with it and to see if I can find the dual boot to WinXP

One last question and you may have answered it already.
My changing the CMOS - order of Boot Device Sequence, wouldn't have made the PC boot to WinXP... I would have to edit that Config file to go to the other partition using Grub> Edit (I forget the exact details but have them printed off).  Right?

I probably should change the Boot Sequence back to the original setting then?
thanks,
Greynold

---

### Post by ejket on 2008-02-05
> **Greynold said:**
> Just heard from son... Once he heard system was coming up Ok! and asking for PWD -- don't think he wants me to pursue any further.

I'll still look at some of the settings you guys have replied with just to see if I can gain a little more familiarity with it and to see if I can find the dual boot to WinXP

If I understand this correctly, you haven't actually logged in to the system because he doesn't want you to (or you don't have a password).  If you have the disk he installed kubuntu from, you can run it live and look at the machine that way, using the recommended commands.  It's a very good idea to know what's on the machine before you start reinstalling everything.

> **Greynold said:**
> One last question and you may have answered it already.
My changing the CMOS - order of Boot Device Sequence, wouldn't have made the PC boot to WinXP... I would have to edit that Config file to go to the other partition using Grub> Edit (I forget the exact details but have them printed off).  Right?

I probably should change the Boot Sequence back to the original setting then?
thanks,

Is there more than one drive?  It seemed to me that you were referring to different partitions on the same drive, in which case I don't know what you changed in the BIOS.

In any case, you shouldn't need to do anything directly with grub if it boots to an existing partition, since the work you'd need to do would be with /boot/grub/menu.lst ...but first find out whether XP is there or not for sure.

---

### Post by Greynold on 2008-02-05
Originally in the CMOS setting for the Boot Drive sequence it had:
1.4M-JLMS XJ HD166S
2.(the Floppy designation, and then)
3.MAXTOR 6Y080LD (which I took for the original WinXP partition)
4.(the CD drive designation.)

In the CMOS Disk Drive configuration/settings I got a little confused when I saw both drive names configured at 81.9Gb/each -- and the MAXTOR drive is only an 80Gb drive -- but, I may not be remembering something accurately; I suppose it could've been 81.9Mb.  I'll double check that tonight.

I was just hoping to be able to run some disk diagnostics/repair utility on the disk to verify reliability as Son was indicating that it was failing on Startup... He wasn't even getting to User/PWD prompt.
Does this help clarify what I thought should be done.  
Usually, on my PCs I clean out all the junk, perform a ScanDisk and then a DeFrag.
I don't really care what's on the drive at all - just wanted to be sure it is reliable.

I did get an automatic (what I believe to be a ScanDisk operation executed after I restarted the system some 10-15 times) -- Said it had been restarted 30 times and this process was automatic on the 31st startup.  It all worked to 100% completion on the Percentage Progress display; then, it just booted to the User and PWD prompt.

---

### Post by Nythain on 2008-02-05
that was an fsck check, sort of like a scandisk, that gets forced every X number of mounts per partition... if it worked to 100 and didnt spit out any errors or report any problems, then you are good on data integrity on that particular partition more than likely... im nto sure how in depth fsck gets as far as checking for physically bad sectors or damaged parts of teh drive itself though, or if it even does at all for that matter...

---

### Post by MasterXandrex on 2008-02-05
OK, I have a few suggestions. 

1) Regarding changing the boot order in the BIOS, this will have no effect unless he has setup XP on a different bootable partition. Since you have switched it to no avail, this is not likely the case.

2) Unless, like you said, your son blew away the boot entry for XP (perhaps along with the partition or perhaps not) it should be in the boot menu.

3) Regarding the test you see from the GRUB menu, if I am understanding correctly this is Memtest86 which Google defines as:
>  Memtest86+ is software designed to stress-test an x86-compatible computer's random access memory for errors
Which is, I believe, self-explanatory.

4) Regarding not know the password there are ways to get past that... it sounds like your son doesn't want you getting into his former account (not judging just saying it is up to you whether or not you actually do this). Here are the instruction as I know them (let me know if you need clarification):

```

1) Go into the BIOS and set the first boot device as the CD-Rom
2) Insert a live CD and boot into (K)Ubuntu live
3) Open a terminal and type **sudo -s**, this make you root (the god-like administrator, for the purpose of the open terminal session. 

Next you need to mount your hard drive to a directory if this is not already done, I don't remember if the live CD will do this automatically. *If it does, skip steps 4 and 5 and replace "/mnt/hard_drive" with the mounted directory. If you are not sure do step 5a.*

4) **mkdir** **/mnt/hard_drive** --this make the folder hard_drive in the folder mnt
5a -- Optional, see above) **umount /dev/hda1**
5b) **mount /dev/hda1 /mnt/hard_erive** -- the mounts the device hda at the hard drive folder 
     **_*Note: hda may not be the right device, but is the usual device for the first IDE hard drive. But as your alternative is to format you have little to lose. You may also try hdb1, sda1, or sdb1 where '1' can be any number from 1-4*_**
6) **chroot /mnt/hard_drive** -- if this does not work you are not in the right place try an alternative step 5.
7) After this, type **passwd *username***. -- *username* being your son's username. If you don't know your son's username **ls /home** and see if any entries look familiar.

This should reset your son's password, simply reboot and try what you entered as the new password.

```


Hope this helps,

Xan

---

### Post by neurostu on 2008-02-05
If you are just looking to get a brief experience with linux the best thing to do would be to get your hands on a Live CD. This will let you load UBUNTU off the cd without installing it, You can muck around with things without damaging your computer.

---

