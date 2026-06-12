---
title: "Installation Trouble"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-05
This is my first post and I don't know if this is the right place to ask my question, so sorry if it isn't.

Anyway, I burned a live CD or whatever it's called and ran it on my computer. It worked fine, so I backed up most of my files and started the installation.  When it hit about 82% it didn't move for a long time, so I cancelled it (probably bad?). I restarted my computer without the CD and it said it couldn't load the operating system or something along those lines. I put the CD back in and rebooted and decided to try again. This time, it showed the partition size at around 65% and 7gb, last time I did this it was at 70+gb, so I think something got screwed up there. I told it to install anyway and it was at resizing partition for the longest time, so I just closed it and stopped trying. I originally planned to dual boot with windows (never used Linux before) and [http://whylinuxisbetter.net](http://whylinuxisbetter.net) gave me an Ubuntu link and said if I just followed the directions it would keep windows. But the could not load operating system message made it seem like windows was gone. I'm afraid to tell it to erase my HD and install because

1) I don't know if Windows is still there or not.

2) My system restore is on a partition and not a CD.

I don't know that much about computers, so if you need any more information just ask and I can see if I can find it.

Any help is appreciated, thanks!:confused:

---

### Post by Biscuitpie on 2007-04-05
I have no idea how to fix this and my computer is useless to me right now...

---

### Post by h0ax on 2007-04-05
When you started the original install, if you didn't define separate partitions for Linux/Windows and let it start, it over-wrote what was on your hard drive.
Merely running the LiveCD has no impact on your hard drive.

If you boot into the LiveCD and try to look around, run fstab in the terminal and see what your partition table looks like.  If it does not have something with NTFS, then the Windows partition is not there X_X.

This could be bad.
Check that fstab command and let us know what it says.

---

### Post by Biscuitpie on 2007-04-05
I opened terminal and typed in fstab and nothing happened; I don't know what to add, because as stated before I'm not great at computers. BUT, I went back to install and opened manually edit partitions as I think that's the same thing. I took a picture with my phone (the top 2 are ntfs).

---

### Post by Razorback on 2007-04-05
Looks like Windows is still there.  You made need to fix your MBR, as the Linux will install GRUB to handle that.  If you get your hands on an XP install CD you can probably fix this fairly easily.

---

### Post by Biscuitpie on 2007-04-05
I'm new to Linux and not advanced at computers so I have no idea what MRB and GRUB are. I have a copy of XP laying around somewhere, but I really don't want to have to erase some of the games and stuff on there. Also, I want Linux to work and be able to dual boot, etc, so reinstalling Windows is not my main problem. Linux never installed correctly. It'd be great if I got some help with all of that. :( Sucks to be a noob.

---

### Post by Razorback on 2007-04-05
What I meant is that you can still possibly save your XP install.  I have had a Ubuntu install fail on me before and it turned out to be a bad CD.  I burned a new one and all went perfectly.  You can check your install CD to make sure it is OK, as it is one of the selections when ubuntu starts up.

BTW - what is the size of your hard drive?

---

### Post by Biscuitpie on 2007-04-05
So, what you mean is, by reinstalling XP I will keep my old files like upgrading to Vista?

Also, I will try the test to see if it works.

Some other information I'd appreciate:

How to set it up to dual boot

How to clear up some partition space or whatever because it went from 70gb to 7gb and I guess what I'm asking is how do I uninstall any files that I got on there?

---

### Post by Razorback on 2007-04-05
Are you running XP or Vista?
What is the size of your hard drive?
There are two partitions in your post that are 72 GB and 7 GB.  They are NTFS and are probably your Windows install.  To dual boot, you will need to complete the Linux install and use GRUB (which installs with Ubuntu).  There is a little work involved but is pretty easy.  I am doing that now on one of my machines.

And I am not saying you should reinstall Windows.  I would try to get Ubuntu installed since you have gone this far.

---

### Post by Biscuitpie on 2007-04-05
Eh, the check said nothing was wrong. I have XP and a 100gb hard drive (laptop) but I have a 250gb external that will maybe help? Also, I have a Sony VAIO (yeah, keep laughing) and I don't know how to get into the recovery partition or BIOS for that matter. F2 and Del do nothing and my dad said that the XP we have is older than the one that came with my computer and it will screw it up. Though, I don't think he knows much about computers, and he won't tell me where our disc is.

---

### Post by Biscuitpie on 2007-04-05
Eh, so would using our XP disc be bad? Is there anyway to open up my restore partition from the LiveCD?

---

### Post by louieb on 2007-04-05
Oh I love it. Don't know much  about computers. but I think I'll try Linux without doing any research. Get a Ubuntu CD, boot it, click install and see what happens. You sound like my kind of guy.

Well first lets see if you can get XP fixed. 
Find you XP CD. It has an option to do a recovery install. I've had some success using it that way.

If that fails I glad you have a backup of your data. At least you don't have to try and get it copied off.
 Because reinstalling XP is probably going to happen.  Your first attempt to install probably messed up your windows partition and Your second attempt to install probably did something to your partition table. There is a program called Parted that tries to guess what the table should look like  and attempts to fix it. Its pretty good but it doesn't work 100% of the time. 

If you have to reinstall XP it would be the perfect time to plan your partitions prior to installing anything. There are two links in my signature that you should look at one is psychocats  (see the plan partitions page). and the other is the Dual Boot link. go ahead and look at this page now  its about fixing Duel boot problems [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Just remember if it breaks you get to keep both pieces.

---

### Post by Biscuitpie on 2007-04-05
:) Would reinstalling XP mess up my registry as he said, because it's older. I HIGHLY doubt it. He was good at computers back in the day, but he doesn't keep up with that stuff. Heck, he thinks reformatting is bad for your computer when it's really healthy. :P

---

### Post by oilchangeguy on 2007-04-05
when you reinstall you won't mess up your registry, because you'll be creating a new one. and by an older version of xp what do you mean? it has sp1 and not sp2? that's ok that's what [www.microsoft.com](www.microsoft.com) is for.

---

### Post by Biscuitpie on 2007-04-05
> **louieb said:**
> Oh I love it. Don't know much  about computers. but I think I'll try Linux without doing any research. Get a Ubuntu CD, boot it, click install and see what happens. You sound like my kind of guy.

Well first lets see if you can get XP fixed. 
Find you XP CD. It has an option to do a recovery install. I've had some success using it that way.

If that fails I glad you have a backup of your data. At least you don't have to try and get it copied off.
 Because reinstalling XP is probably going to happen.  Your first attempt to install probably messed up your windows partition and Your second attempt to install probably did something to your partition table. There is a program called Parted that tries to guess what the table should look like  and attempts to fix it. Its pretty good but it doesn't work 100% of the time. 

If you have to reinstall XP it would be the perfect time to plan your partitions prior to installing anything. There are two links in my signature that you should look at one is psychocats  (see the plan partitions page). and the other is the Dual Boot link. go ahead and look at this page now  its about fixing Duel boot problems [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Just remember if it breaks you get to keep both pieces.

Ok, installing XP now. After that should I delete the Linux partitions. Would I just need Parted for that?

Second, that page is about fixing dual boot right? Can you tell me how to set it up. I don't think I'll just click OK this time.

---

### Post by Biscuitpie on 2007-04-05
> **louieb said:**
> Oh I love it. Don't know much  about computers. but I think I'll try Linux without doing any research. Get a Ubuntu CD, boot it, click install and see what happens. You sound like my kind of guy.

Well first lets see if you can get XP fixed. 
Find you XP CD. It has an option to do a recovery install. I've had some success using it that way.

If that fails I glad you have a backup of your data. At least you don't have to try and get it copied off.
 Because reinstalling XP is probably going to happen.  Your first attempt to install probably messed up your windows partition and Your second attempt to install probably did something to your partition table. There is a program called Parted that tries to guess what the table should look like  and attempts to fix it. Its pretty good but it doesn't work 100% of the time. 

If you have to reinstall XP it would be the perfect time to plan your partitions prior to installing anything. There are two links in my signature that you should look at one is psychocats  (see the plan partitions page). and the other is the Dual Boot link. go ahead and look at this page now  its about fixing Duel boot problems [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Just remember if it breaks you get to keep both pieces.


I forgot, what should I do in the recovery console? Just leave and reinstall? My only issue with that is reinstall WoW, getting patches, getting addons, and reconfiguring those, that'll be a pain. But if I don't have to, it would be great.

---

### Post by Francesca-chan on 2007-04-05
i have to install linux Ubuntu on my computor but it keeps freezing. I boot my comp with the cd in and i press enter to "start or install ubuntu" and the page loads. 
here' my problem it freezes when i click on the install icon. 
it works for about 15 minutes then everything jams, freezes, w\e.

any hint on what could be the problem? 

i'm working on a dell, with a pentium II, and 512 RAM....

---

### Post by Biscuitpie on 2007-04-05
> **Francesca-chan said:**
> i have to install linux Ubuntu on my computor but it keeps freezing. I boot my comp with the cd in and i press enter to "start or install ubuntu" and the page loads. 
here' my problem it freezes when i click on the install icon. 
it works for about 15 minutes then everything jams, freezes, w\e.

any hint on what could be the problem? 

i'm working on a dell, with a pentium II, and 512 RAM....

That's kinda like what happened to me. It froze on 82% and every time I clicked on install after that, it froze. =/

Anyway, I guess since nobody is replying I won't try to recover XP and I'll just reinstall it, but I will need some help setting up dual boot, IE something I can understand. :lolflag:

---

### Post by Razorback on 2007-04-05
> **Biscuitpie said:**
> That's kinda like what happened to me. It froze on 82% and every time I clicked on install after that, it froze. =/

Anyway, I guess since nobody is replying I won't try to recover XP and I'll just reinstall it, but I will need some help setting up dual boot, IE something I can understand. :lolflag:

You probably messed up the MBR (master boot record) on your hard drive as I stated earlier.  You can use your windows CD to try to repair your MBR using the fixmbr command inside the recovery console.  

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

If you plan to reinstall XP I would setup your hard drive partitions to you can easily segregate your XP and linux installs.  I actually use two separate hard drives.

---

### Post by Biscuitpie on 2007-04-05
Well, the whole thing that started this is that I know nothing about partitions (well I know what they are, basically). If you could tell me how to set those up OR get linux on my external harddrive (would it be slower?) that'd be great and I'd probably be done, but one of the other reasons this happened is that the install was frozen on 82%. The diagnostic thing said my disc was fine... so, any recommendations?

---

### Post by Razorback on 2007-04-05
Have your reinstalled XP?  Did you use the whole disk to install or part of it?

---

### Post by Biscuitpie on 2007-04-05
Actually, no I haven't installed it. I got to a partition page, lol. I have 2 unknown, one NTFS, one unpartitioned, and an EISA utilities one (probably my recovery). Not counting my external. Should I delete the two unknown as they are probably Ubuntu? And then how should I set it up?

---

### Post by Razorback on 2007-04-05
> **Biscuitpie said:**
> Actually, no I haven't installed it. I got to a partition page, lol. I have 2 unknown, one NTFS, one unpartitioned, and an EISA utilities one (probably my recovery). Not counting my external. Should I delete the two unknown as they are probably Ubuntu? And then how should I set it up?

Are you going to reinstall or do you want to try to recover the XP install?  Answering this would change what I would suggest.

---

### Post by louieb on 2007-04-05
Pardon me I was rocking out to some 1970's Dire Straits. A couple of questions about the freeze you are having. Which version of Ubuntu are you installing? I just installed Feisty beta this morning and it stopped a couple of times for a while.   But I noticed the router lights blinking so I guess it was getting something from the net. Did you see any sign of internet activity?  Hum what next Santana, Steely Dan or maybe so Outlaws?

Did you check psychocats partition planning page. Its **a lot** easier to set up a dual boot system if you go ahead and partition the hard drive  before installing anything. My favorite partitioning tool is the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). Oh Heavy Fuel playing now check back later.

---

### Post by Biscuitpie on 2007-04-05
Just gonna do a reinstall and make it nice and small for faster gaming.

---

### Post by Biscuitpie on 2007-04-05
What I need to know is what to do for partitions on the blue screen AND linux install because it confused me with saying make something for root.

Checking psychocats now.

---

### Post by Biscuitpie on 2007-04-05
I must seem like a complete moron, but do I burn GParted to a disc or what exactly am I supposed to do? I feel like such and idiot.

---

### Post by louieb on 2007-04-05
> **Biscuitpie said:**
> I must seem like a complete moron, but do I burn GParted to a disc or what exactly am I supposed to do? I feel like such and idiot.
Remember experience is something you get after you need it.  But yea to burn it to a CD just like you did with the Ubuntu iso. 

If everything went right you wouldn't be having this much fun. 
[http://www.google.com/linux](http://www.google.com/linux)  <-- search here for partition and get an idea of what are  primary, extended, and logical partitions. It will help you understand the what and why of what you are doing. 
How big a hard drive do you have? I'll get back with a idea of how to partition it.

---

### Post by Biscuitpie on 2007-04-05
> **louieb said:**
> Remember experience is something you get after you need it.  But yea to burn it to a CD just like you did with the Ubuntu iso. 

If everything went right you wouldn't be having this much fun. 
[http://www.google.com/linux](http://www.google.com/linux)  <-- search here for partition and get an idea of what are  primary, extended, and logical partitions. It will help you understand the what and why of what you are doing. 
How big a hard drive do you have? I'll get back with a idea of how to partition it.

I have a 100gb and a 250gb external (I used it for my backup, but it was mainly a couple thousand songs). I deleted one partition I knew was linux, but another says it may prevent an OS from starting and it's MBR or something. Should I delete that too? Seeing as I'm gonna retry starting up Linux, I should have as much partition space as possible, am I right?

---

### Post by Biscuitpie on 2007-04-05
Hopefully this will be resolved son.

---

### Post by louieb on 2007-04-05
Almost forgot how good the Ventures are.
OK unplug the external not going to need it now and don't want to have an accident.
Use the GParted CD first. Delete all the partitions on the drive leaving 100% unallocated space.
Now you are going to create 4 partitions you are just going to have to decide how much of the drive to give to each.[LIST=1]
[*]1st partition for widows let GParted format it fat32 or NTFS it really doesn't matter. You are going to let the windows install format it later. (minimum size 10 gig may want to give it up to half the drive)
[*]2nd partition for Ubuntu format it ext3 again it really doesn't matter. You are going to let the Ubuntu install format it later. (5 to 7 gig)
[*]3rd partition for Ubuntu's /home format it ext3. use all but 1/2 to 1 gig of the remaining space.
[*]4th partition for Linux swap. format it Linux swap.  1/2 gig swap should be plenty.[/LIST]Click on the apply button and let GParted do its stuff. When its done leave the GParted CD in and reboot the computer. If everything looks ok then it time to install windows. Haven't install XP in a while but you should be able to tell it to install itself in the first partition and let it format the partition. 

When you get Windows installed and running. Post back and I'll go through how to use the partitioner in the Ubuntu installer. Can't tell you until I find out which version of Ubuntu and if you have: the live CD or the alternate CD.

---

### Post by Biscuitpie on 2007-04-05
So, GParted is used from boot? And I was using the LiveCD.

---

### Post by Biscuitpie on 2007-04-05
Ok... I don't think it starts at boot, because it didn't do anything. Maybe I burned it wrong.

---

### Post by Biscuitpie on 2007-04-05
I burned it just like I did the Ubuntu CD. Any ideas?

Eh, the program I had used was Ifra something and it had a special ISO thing. That's what I need, but I can't find it.

---

### Post by louieb on 2007-04-05
Using windows I guess? get [Burncdcc]("http://www.terabyteunlimited.com/utilities.html") thats all it does is burn an iso to a CD. Its what I use in windows. [Heres my page on burning an iso file to CD. ]("http://louboldt.com/ilinuxiso.htm")

---

### Post by louieb on 2007-04-05
When you get done installing XP and have verified it works. You can start installing Ubuntu. Enter the stuff it asks for until you get to the partitioning screen. At that point you are going to choose manual partitioning. 
The first screen will look like the GParted screen. Since you have already partitioned your drive you won't do anything on that screen. The next screen is where you tell where to mount the partitions. 
It may have guess right at the mount points for the 4 partitions. There will be some drop down lists on that screen 2 lists for each partition. also there will be a check box asking if you want to format the partition. 
One of the columns will list the partition and look like /dev/hda1 or it may be /dev/sda1 any way before you leave that screen it should look something like this:
```

partition        mount point           format box
/dev/hda1     /media/windows      format box unchecked      
/dev/hda2     /                              format box checked      
/dev/hda3     /home                     format box checked
/dev/hda4     swap                       format box checked

```Once you get it looking like this your ready to install. Just go for it and see what happens. It should work

---

### Post by Biscuitpie on 2007-04-05
Got that to work, but when it loads I get a ton of options. Which should I do?

EDIT: Gparted that is.

---

### Post by Biscuitpie on 2007-04-05
Gonna bump this as we were typing at the same time before.

---

### Post by louieb on 2007-04-05
Look at post #31.  and  get  you partitions set up.  Look at the GParted doc if you need to. But if you just click around it will be apparent how to used GParted to get your disk partitioned. Got to mow the yard now. I'll get back later.

---

### Post by Biscuitpie on 2007-04-05
Apparently I need to put in a Windows disc because it couldn't read it. Yet it's only telling me that BECAUSE I put XP in.

---

### Post by Biscuitpie on 2007-04-05
A new XP is "on the way". Thanks for all of your help. :)

---

### Post by Biscuitpie on 2007-04-05
At the start of the Virtual CD it always says Enabling NRG or RNG don't remember and it says it can't and it's aborted. But a line down it says OK. Is that fine? About to install.

---

### Post by louieb on 2007-04-05
Ok I guess you got XP installed. and now the Ubuntu Live CD desktop is up. go back to post 36 and  set your mount points the way I described and you should be fine. I'll check back in the morning and see how it went. Good luck.

---

### Post by Biscuitpie on 2007-04-06
I have Ubuntu installed and am on it right now. BUT, I can't install Windows. When it is finished loading everything at the blue screen (not an XP screen, I mean the boot one) it will say Setup is starting Windows... and never finish. The disc works fine on my dad's computer. Any ideas?

---

### Post by louieb on 2007-04-06
Did you install XP before Ubuntu? OR are you trying to install it now? 
need 2 things then maybe I can suggest something..
Open Applications>accessories>terminal> and run ```
sudo fdisk -l
``` (as in little). and copy and past the the output here. This list your partition table.

And I want you copy and paste the file /boot/grub/menu.lst.
Open Applications>accessories>text editor
Pretty much like like windows  Click the open button > Choose File System > Choose boot folder > choose grub folder ....
Going to work --- later.

---

### Post by Biscuitpie on 2007-04-06
I put my password in but it doesn't work...
I tried Windows both before AND after.
Here's the file:


```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0c57934c-b91d-452f-9f59-19311f29c2b2 ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single
QUOTE
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Biscuitpie on 2007-04-06
Eh, got it thanks to another thread. :) 

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4110    33013543+   b  W95 FAT32
/dev/sda2            4111        5028     7373835   83  Linux
/dev/sda3            5029       12018    56147175   83  Linux
/dev/sda4           12019       12161     1148647+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)
```

---

### Post by louieb on 2007-04-06
Everything looks fine,  fdisk looks normal, menu.lst looks normal. Which XP disk do you have? I really don't have a clue why the XP CD won't work on your computer. I did a quick search of the Microsoft knowledge base and came up  with this [http://support.microsoft.com/kb/811267/en-us](http://support.microsoft.com/kb/811267/en-us) 
Don't have anything better that to suggest you browse around the microsoft site. 
Sorry and good luck.

---

### Post by Biscuitpie on 2007-04-06
Well, thanks for all of your help. I'll try again, =/

---

### Post by Biscuitpie on 2007-04-06
Well, I went back to the first CD and got to the part where it said I need to put a disk back in, so I then switched to the other CD. I then told it to format the first partition to NTFS. It told me to put the other disc back in, so I did (it said put home in, the second one was pro). It's now formatting. :) Gonna need that GRUB fix link thingy, though.

---

### Post by louieb on 2007-04-06
> **Biscuitpie said:**
> :) Gonna need that GRUB fix link thingy, though.
Cool the GRUB fix thread is in my signature.

---

### Post by Biscuitpie on 2007-04-06
Well, I don't think that it installed right. I can't seem to get my internet to work. It says my card is disabled or something. =/

---

### Post by Biscuitpie on 2007-04-06
So, I guess I'm screwed in that department. :'(

---

### Post by louieb on 2007-04-07
> **Biscuitpie said:**
> Well, I don't think that it installed right. I can't seem to get my internet to work. It says my card is disabled or something. =/
Didn't get  what installed right XP or windows? 
Did you get it Duel Booting?
In XP right click on my computer> services and applications > services
find **dhcp client** and see if it is started.

---

### Post by Biscuitpie on 2007-04-07
> **louieb said:**
> Didn't get  what installed right XP or windows? 
Did you get it Duel Booting?
In XP right click on my computer> services and applications > services
find **dhcp client** and see if it is started.

I think I need drivers.

---

### Post by Biscuitpie on 2007-04-07
I did that and it was started. I went to a setup wizard and it said my hardware was disabled or something.

---

