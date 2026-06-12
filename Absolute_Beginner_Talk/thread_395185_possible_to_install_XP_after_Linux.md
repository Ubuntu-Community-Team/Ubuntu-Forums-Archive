---
title: "possible to install XP *after* Linux?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-27
Argh.

ARGHH!!!

After taking the plunge and wiping my system HDD, I installed Ubuntu and a couple of weeks later am finally able to take enough time to sort through some of the issues I have. And *now* I read that I should have installed XP first and *then* installed Ubuntu. 

My magic plan was to partition everything so that Ubuntu has 10gb in ext3, XP has 10gb in NTFS, my XP games will have about 30gb in NTFS and the rest of the drive (in ext3) for MP3's and backing up and moving all the rest of my files from my second physical HDD.

Is there any way to safely install XP after already installing Ubuntu?

I *do* have to HDD's so I suppose I could back up and wipe the other drive, install XP on that and have Ubuntu on its own physical drive. That would be the easy (I think) but tedious option, because I'd have to sort and back up loads and loads of files. Are there any other options?

---

### Post by x1a4 on 2007-03-27
Hi,

The short answer is No.  

Windows doesn't play well with others.  It doesn't bother checking for non-M$ operating systems and forces itself on your hard drive.

---

### Post by simonn on 2007-03-27
My, albeit limited, experience is that if Windows sees a non-Windows partition on the drive you want to install it on it simply will not install.

---

### Post by link141 on 2007-03-27
Did you already install Windows?  There actually **is** a way to install Windows XP second, but it involves modifying your master boot record by reinstalling grub.  It really isn't that hard to do.  If I were in your situation, I'd just install Windows second.  Oh, and I don't think you can (without a lot of work) install and run windows on a slave drive.  If you want me to give you directions on how to install Windows XP second, just post a response, and I'll be happy to help :). 
Good luck.

---

### Post by nudnik on 2007-03-27
In agreement with earlier posts, I would have to say in my experience, its not possible. Ubuntu will do a nice job of resizing an NTFS partition if you install it after XP. If you have Vista, I would suggest allocating an entire drive to it as it seems to be utterly incompatible with Linux at this time. GRUB will not recognize it.

Of course, I imagine if you only allocated, say, half of the disk to Ubuntu, then it might indeed be possible. I think most of us are assuming you have created Linux partitions which span accross most of the disk and are hoping XP can resize them.

---

### Post by tux_rox on 2007-03-27
@link141:

I don't know about toecutter, but I'd like to see your directions... (if it's not a huge hassle).

Thanks!

---

### Post by mr. deeds on 2007-03-27
I've managed to do it in the past.  Though I had Windows on a different hard drive and had to edit the GRUB under the boot path.

---

### Post by toecutter on 2007-03-27
> **tux_rox said:**
> @link141:

I don't know about toecutter, but I'd like to see your directions... (if it's not a huge hassle).

Thanks!

Yeah I wouldn't mind seeing a walkthrough either :)

@ nudnik - my boot HDD is set up like this right now:
10gb - Ubuntu
2gb - swap
10gb - where i was hoping to install XP
30gb - where I was going to install XP games
rest of drive (45gb) - multimedia files

I *could* swap the two drives on the IDE cable to install XP on the second physical drive I have, I'd have to back up some stuff but it's not impossible. Then I could fiddle with GRUB somehow to make the dual-boot work, I'm assuming...

Crikey. I'd really not have to re-install everything on Ubuntu but to be honest I've only been playing around with it an hour or so a day (on average) the past 2 weeks so I suppose I could just wipe the hard drive again and start from scratch...

I'm just not sure which of the two options above would be easier and/or faster :) 

bleah...

---

### Post by link141 on 2007-03-27
[quote=simonn] ...if Windows sees a non-Windows partition on the drive you want to install it on it simply will not install. [/quote]

When your installing windows (like from a recovery disc) it should give you the option of which partition to install windows to (I know this from experience).  It will just ignore the other partitions that it doesn't recognize.

[quote=nudnik] In agreement with earlier posts, I would have to say in my experience, its not possible. [/quote]

As far as I know, as long as you install XP to it's own NTFS partition, it should be possible.  As long as you reinstall grub afterwards, it should work...

I'm probably going to end up putting Xtra Putrid on my computer at some point in the future, so I'll see how it goes, and post a response.

---

### Post by link141 on 2007-03-27
I'm in the process of typing up the directions, and will post them shortly.  I've got to run out quick, but I'll be back soon...

---

### Post by toecutter on 2007-03-27
Awesome, can't wait! :) Like I said, I don't have much keyboard time with the Ubuntu install, and everything from the first HDD is backed up, so if it all goes wrong then I'll just wipe it all again and install the dual-boot system as recommended by everyone else, so I'm willing to give anything a shot right now.

---

### Post by link141 on 2007-03-27
I've decided to test my directions, and install Windows XP on my Machine.  I'll see how it goes, revise my mini how-to if necessary, and post it in this thread.  Thanks for your response, :) it's nice to know that my help is appreciated :).  
Like the terminator, I'll be back! :)

---

### Post by kinson on 2007-03-28
<Edit : Quoted wrong post>

As to restoring GRUB after installing windoze, you might wanna follow the instructions on this thread:

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub")

Hope that helps.

---

### Post by Doug11 on 2007-03-28
> **link141 said:**
> Did you already install Windows?  There actually **is** a way to install Windows XP second, but it involves modifying your master boot record by reinstalling grub.  It really isn't that hard to do.  If I were in your situation, I'd just install Windows second.  Oh, and I don't think you can (without a lot of work) install and run windows on a slave drive.  If you want me to give you directions on how to install Windows XP second, just post a response, and I'll be happy to help :). 
Good luck.

You are right, it's actually quite simple, three or four easy commands from the terminal in a Live CD.

> **nudnik said:**
> In agreement with earlier posts, I would have to say in my experience, its not possible. Ubuntu will do a nice job of resizing an NTFS partition if you install it after XP. If you have Vista, I would suggest allocating an entire drive to it as it seems to be utterly incompatible with Linux at this time. GRUB will not recognize it.

Of course, I imagine if you only allocated, say, half of the disk to Ubuntu, then it might indeed be possible. I think most of us are assuming you have created Linux partitions which span accross most of the disk and are hoping XP can resize them.

Grub DOES recognize vista. I am dual booting Vista and Ubuntu. Had a little problem at first because I resized my Vista partition with GParted and but after I got that going I had to reinstall grub and now when I boot, I have the option of booting either of my two linux kernels or M$ vista/longhorn. As far compatiblity, I'm not quite sure on that. Haven't got into the networking stuff yet.

---

### Post by Malac on 2007-03-30
Download FreeDOS FDisk to a bootable DOS floppy run it and choose the option to hide your Ubuntu partition then run install, XP don't even know it's there.
Run FDisk Floppy again un-hide Ubuntu partition. Reboot to Ubuntu then update grub, viola.
Dead Easy. :)

---

### Post by DaemonLee on 2007-03-30
My quick idea would be to do the following;


Use GParted to make a NTFS partition, and install Windows XP on that. You'd make this partition by resizing your main one (/) or whichever you wish. 


The Grub alteration, welll....Your on your own there..

I just answered the easiest part that seemed to be the most obvious. :)

---

### Post by DoorGunner on 2007-03-30
You might think about saving your email and shortcuts and what ever else you need to save prior to any XP experiment......Just to be on the  safe side

---

### Post by Malac on 2007-03-30
> **DoorGunner said:**
> You might think about saving your email and shortcuts and what ever else you need to save prior to any XP experiment......Just to be on the  safe side
Yeah The Transfer Wizard is actually quite good for this. Blimey MS doing a useful program.

---

### Post by link141 on 2007-04-01
Sorry I took such an incredibly long time to post the mini-howto I promised, I've been kind of busy...  Anyway, here it is:
[size=+2]Installing Windows[/size]
[list=1]
[*]Make sure you've backed up all your data, as I can't guarantee this to work.
[*]Install Ubuntu first just to cause trouble :).
[*]Make sure you have a blank NTFS (or fat32*) partition on your harddrive.
[*]Optional: If you want to follow malac's idea (thanks malac :)), use the [super grub disc](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk) or free dos fdisk (couldn't find page) to hide your ubuntu partition.  Follow D in the next set of directions  
[*]Insert your Windows XP install/recovery disk into your computer, boot into it, and wait for it to load it's drivers and everything.
[*]A menu will come up with three options. Press enter to choose the "set-up Windows now" option, and agree to the license.
[*]An overview of your harddrive will show up, displaying all your partitions (windows will show non FAT or NTFS partition types as "unknown").  Choose the NTFS or FAT partition that you want to install Windows on, and tell the installer to leave the filesystem intact. 
[*]Let the installer scan the disks, copy files, and reboot.  Leave the CD in the disk drive, but don't boot into it again.
[*]A graphical installer will come up to finish the installation process, occasionally asking you to give some information for the install.  Once it's finished installing the files in this step, it will automatically reboot.
[*]When it boots back up, it will ask you to set-up users and some other things (like register Windows :rolleyes:).  Once finished, it will log you into XP, and you can now use it.
[*]You can now remove your XP install disk.  Reboot your computer to make sure it installed correctly. (You may want to wait before updating windows, and installing your programs)
[/list]
You now have windows installed, and can proceed to the next set of directions.
*You can use a fat32 partition to install windows on, which will enable you to read/write to it in Ubuntu out-of-the-box, but fat32 is not a journalled filesystem, meaning that if your computer is shutoff during a storm or something, and it happens to be writing some data to the disc when this happens, the whole partition gets messed up, and you lose all your data.

[size=+2]Getting Grub to work again[/size]
I'll give you instructions on how to use the super grub disk to re-enable grub again, but I will also post the links here that everyone posted on this thread (thanks guys!:)) 
[list=A]
[*][size=+1]Using the  [super grub disc](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)[/size] (further down the page, it will give you the same directions)
[list=1]
[*]Insert the super grub disk into your computer, and boot into it.
[*]Choose your language
[*]Choose GNU/Linux
[*]Choose fix boot of GNU/Linux (notice how it says "Has windows overwritten your MBR?")
[*]Select the partition you have linux on.  If SGD was successful, it will tell you that it succeeded
[*]Reboot, and remove the SGD disk.
[/list]
Grub is back! Yay!
[*][[size=+1]Restore GRUB (if your MBR is messed up)[/size]](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub) (link posted by kinson) this is a rather old how to, so the first post used the old text installer that was in Hoary.  However, you can still do it using the Alternate Install CD.  This is probably the easiest way to install grub if you have an Alternate Install CD lying around.  You can also follow the directions on another post on that thread with the Live/install CD. 
[*][[size=+1]How to restore Grub from a live Ubuntu cd[/size]](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub) Requires using a terminal, but has easy to follow step-by-step instructions. 
[*][size=+1]Hiding your Ubuntu partition, and updating grub[/size]
[list=1]
[*]Unhide your Ubuntu partion using the [super grub disc](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)
[*][Setup grub within ubuntu](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub) (live CD or direct Boot)
[/list]
[/list]

[size=+2]None of these worked![/size]
In the unlikely event that none of these how-tos worked, and you still can't boot ubuntu, then you might want to try using the [super grub disc](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk) to boot Ubuntu directly. 
[list=1]
[*]Boot your computer off the [super grub disc](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk).
[*]Choose your language
[*]Choose GNU/Linux
[*]Choose Boot GNU/Linux Directly
[/list]
From here, you can retrieve your data, do any important work, or try to fix grub from Ubuntu.

Well, there it is.  I hope someone finds this useful.

---

### Post by confused57 on 2007-04-01
Nice writeup...it gave me an idea about "hiding" Ubuntu, if just reinstalling grub doesn't work after installing Window's.
Wonder if you can put an extra line in your Window's grub entry to hide the Ubuntu root partition, similar to how it's done for 2 Windows on the same hard drive?:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

be interesting for someone to try, if nothing else works.

---

### Post by toecutter on 2007-04-02
> **link141 said:**
> Sorry I took such an incredibly long time to post the mini-howto I promised, I've been kind of busy...  Anyway, here it is:

Very very cool :) Thanks for the walkthrough! ;D

---

### Post by jorwex on 2008-05-02
The graphical portion never appeared for me. It just went right back to the beginning of the install after the manditory restart.

What should I do?

---

### Post by metrorat on 2008-05-02
Had the same issue myself - you can install XP onto the same hdd as Ubuntu after Ubuntu has been installed but it will overwrite the mbr where the  friendly Grub lives, the upshot of this being that you will only be able to boot into windows when you restart after the XP install.  To sort this out you need to reinstall Grub on to the mbr and have it detect all your OS boot options.  Handily you can download the ISO for Super Grub Disk which does exactly that.  

It is bootable so you simply download the iso from [supergrubdisk.org/]("http://http://www.supergrubdisk.org/"), burn it to disk, check it, install XP, boot from Super Grub Disk, restore grub to MBR and off you go.  You will have boot options in Grub then for Ubuntu & XP.

Worked like a charm for me...  However be aware that Windows will not see any partition formatted in EXT3 so your music etc will not be accessible from your XP Partition - although I don't think you should have any problems installing XP on an HD with an EXT3 partition already on it. I've done this and it works fine.

Hope this helps.

---

### Post by jorwex on 2008-05-02
@metrorat 

Wait...How do I use the super grub disk to get windows to finish the installation? I successfully got ubuntu up and running again using the live disk....

BUT!! I still did not install windows because It wouldn't complete the 2nd half of the install like I said before. I gave up for the night and reinstalled grub. 

How can I get windows to install??

---

