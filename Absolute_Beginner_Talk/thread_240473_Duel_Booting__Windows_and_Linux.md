---
title: "Duel Booting | Windows and Linux"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Viral on 2006-08-20
Hello!

First, I'd like to apoligize for my previous posts, I was just a little excited for Linux.

I've decided, after my friends convincing me, to get Linux, for real. I got that one Linux called Xubunto, or whatever, on that old desktop.

Not working out. It's really laggy, and I hate it. I want ubuntu, and my laptop can support it. However, I DO NOT want to get rid of Windows! I pretty much want it as two seperate OS's.

My Laptop:
- Gateway
- 512 RAM
- 60 gig HD
- celeron processor
- Windows XP

Duel Booting is something I really want to do, and if you could help me out, it would be awesome. I'm really, REALLY new to Linux, but love it already. the 4 workspaces makes it extra awesome, for organization. Now, can you guys help me? I don't know much about computers.

Thanks in advance, Ubuntu Community!

[I don't want to screw up my laptop, I want this as clean as possible :)]

---

### Post by H.E. Pennypacker on 2006-08-20
Viral, welcome to the Ubuntu community, but more importantly, to the world of open source software.

Here's a[ guide on installing Ubuntu]("http://psychocats.net/ubuntu/installing.html") with information on dual-booting by a forum member named aysiu.

Here's[ a video instructional guide]("http://www.digg.com/linux_unix/Ubuntu_Windows_Dual_Boot_Video_Tutorial") which I found with a Google searching using "dual boot Ubuntu".

Furthermore, the Ubuntu Wiki is a great resource.

---

### Post by Viral on 2006-08-20
Wow.

Thanks! However, keep in mind; I don't have any hardware experience of any kind...

I don't want to screw anything up. Can someone give me a "step by step" guide to help me? My computer already boots by a disc, and I have a Linux CD.

**I have a laptop!** If it's of any importance. How do you portion your hard drive?

---

### Post by Viral on 2006-08-21
Sorry for the double post, but I really need help....

Anybody?

---

### Post by Cryonic on 2006-08-21
Read my post here for a dual boot scenario that works well for me (ignore the part about fat32):

[http://ubuntuforums.org/showpost.php?p=1396745&postcount=4](http://ubuntuforums.org/showpost.php?p=1396745&postcount=4)

Installing Ubuntu will take care of the dual boot, if you adjust the partitions manually. I'd suggest you plan your partitions before you start out. The link above explains some of it, a similar link is in my signature. 
If you need more detailed help, just say so.

---

### Post by coderboi on 2006-08-21
The partioning should be part of the install. 

btw, if you like the idea of virtual desktops you can get software called vern from one guy coding that will do the same thing for you on xp.

> **Viral said:**
> Wow.

Thanks! However, keep in mind; I don't have any hardware experience of any kind...

I don't want to screw anything up. Can someone give me a "step by step" guide to help me? My computer already boots by a disc, and I have a Linux CD.

**I have a laptop!** If it's of any importance. How do you portion your hard drive?

---

### Post by seshomaru samma on 2006-08-21
Viral
The link in H.E. Pennypacker's post is very detailed
Please go through it several times before you install, if you have any questions you can post it here.
Especaily make sure you understand the partition bit ,again post specific problems you encounter and we will help you.
Good luck

---

### Post by Viral on 2006-08-21
Thanks!

I've read it several times, and I think... I'm ready. I'm going to back everything up, and then I'm going to go for it.

Here is what I want:

Out of a  60 gig HD:
- 7 gigs for Windows
- 7 gigs for Linux (ubuntu)
- 7 gigs for Backup (came with my gateway...)
- 39 gigs for everything else (CAT32) so I can exchange media between the two.

Good idea? What are your opinions?

EDIT: How do I format my HD that has Windows on it?

---

### Post by Cryonic on 2006-08-21
I'd take ext3 over fat32 for the 39gig partition, and use the tool on [http://fs-driver.org](http://fs-driver.org) to access it from Windows (it just makes you assign a drive letter to the ext3 partition once).
**IF** you want to format your Windows partition (you do realize your Windows installation will be gone?), you can do so while installing Ubuntu, during the manual configuration of partitions and mount points.

---

### Post by Viral on 2006-08-21
Yes, I understand. Why can't I just use FAT32?

So:

After I format my windows drive, and get all my partioning done, what do I do? Exit out of Ubuntu, and try installing Windows?

---

### Post by Cryonic on 2006-08-21
You *can* use fat32, but I just prefer not to, it fragments easily, just to name one reason.

I'd install Windows first (or not, if it's already there, just clean it up). If it's an NTFS partition, you'll have no problem resizing it to 7gig. 

There's one thing you forgot: Ubuntu will need a linux-swap partition, make it 1.5 to 2 times the size of your RAM.

---

### Post by Viral on 2006-08-21
Alright, so, here are the steps (correct me if I'm wrong)

1. Go to My Computer; right click on drive I want to format. Click Format
2. Reboot Computer
3. Reinstall Windows on drive
4. Once Windows is set up boot up Linux
5. partion the HD, resize Windows HD to 7 gigs
6. Make new Partion for Linux of 7 gigs
7. make the rest of the HD be for media; 39 gigs
- Resize Windows partion to 7 gigs
8. Continue through Installation
9. Once Linux is installed, reboot
10. DuelBoot screen will come up! Windows or Linux


How do I resize the windows partion?


Is that right? Am I missing a few steps?

---

### Post by Scunizi on 2006-08-21
If you plan on wiping out the current Windows install, you really can't go to My Computer and format the drive. It probably won't format because you are using that drive to attempt to format.  Essentially you'll re-install windows first choosing the option to "distroy" all the current data on the drive.  Windows will use the entire drive.  Reboot and do all the updates required (abt 3 hrs including SP2.  Next boot from Ubuntu's Live or alternate cd.  I've used both and if you are going to manually set you own partitions, use the alternate cd.  I personally had issues with the logic of the Live version.  The cd will allow you to resize the windows partition to what you want and create the other partitions of the sizes and types you want.  Install Ubuntu and do the updates (apx 40 min).  With the right choices on install Ubuntu will install Grub (boot manager) and write to the MBR so when you boot again you'll be presented with a menu to choose which operating system. If you don't do anything it will automatically boot to Ubunut after a period of time.  Once you've got everything working to your satisfaction, you might want to look into VMWare so you can load your Windows partition inside of Ubuntu.  There's safety in this, in that if VMWare has any issues you can still access Windows through the dual boot screen.

---

### Post by Viral on 2006-08-21
Wow, thanks!

So, I'll download the alternate right now, I appreciate it!

Exactly what options do I have to click for it to load Grub?



In [This page](http://psychocats.net/ubuntu/installing.html), it shows what the partioner will look like.

Now, how would I set the Mount Points on each drive?

I need details, if I screw something up, I'm dead. This computer has my life on it. It's the company's, so I got permission. But still...

So, if I want 4 partions:

- 10 Gigs for Windows
- 7 Gigs for Backup
- 3 Gigs for Linux
- 40 Gigs for Files/Media


And duel boot, what will the Mount Points for each drive?

---

### Post by Scunizi on 2006-08-21
Install should automatically take care of the mounting of the windows partition.  As for the linux side you have to assign a root "/" partition (my personal preferance is 9-12g's.  Better a little too much than too little.), a /home partition (the majority of your disk space for your programs and files), swap (like previously mentioned 1.5 to 2 times your ram).  You can also automatically have Ubuntu use the remaining unused space on the HD after installing Windows.  It will figure out the space for the partitions by itself.  However, it won't create a seperate partition for your /home directory. It will place it with the / partit... not a bad thing but if you hose your linux side and need to reinstall, having a seperate /home partition will save you the time of re-installing most of your programs and set

On a side note, if you just want to try Ubuntu but not constantly run it from the CD, you can use VMWare on windows and install Ubuntu to run within a Windows/window. This won't affect your current setup on your machine.

---

### Post by Tom Brokaw on 2006-08-21
Any particular reason why you want to format your Windows install and then reinstall it?  Or did I just miss something?

---

### Post by Scunizi on 2006-08-21
I'm not really sure why either unless the Windows is getting the normal accumilation of "stuff" that slows it down.  If you decide to leave the current install and put on Ubuntu, back up your windows data including your PST file from Outlook if you are using it.

---

### Post by Viral on 2006-08-21
Thanks for your replies!

Alright, I just free'ed up most of my HD.

my C drive, which is the one I'm going to "split" 3 ways, now has 32 gigs left on it. (plus, windows is installed!)

Current Partions:
- C drive (49.0 Gigs)
  - 32.2 Gigs Free
- D drive (6.82 Gigs) [RECOVERY] I'm leaving this drive as it is
  - 4.15 Gigs Free

________________________

Planned Partions:
- C drive (21 Gigs)
- D drive SAME AS BEFORE (6.82 gigs)
- Linux drive (9 gigs)
- swap drive (1.5 gigs)
- Home drive (17.5 gigs)




so, I'm about to install Linux! Now, let me get this straight: 

Once I get to the partion prompt, I'm going to do the above listings. What filesystems do they use?


correct? I'm about to do this, so quick responses :)

Oh, and what filesystems do each need to be? why do I need "Swap"? and what the file system for Home will be: "FAT32", right?

[How do I tell linux which drive to install on?]

---

### Post by Viral on 2006-08-21
Can anyone help? I'm about to do this!

---

### Post by Scunizi on 2006-08-21
Sorry for the delay... been out working... the linux drive (as you say) is really your "root" or it's also known as "/".  The way you have it split up looks fine.  As for filesystems, the swap drive is only to write currenty loaded portions of programs to the harddisk incase you're running out of RAM.  Ubuntu does it's own thing as far as what file system it uses there.  You can't designate it.  As for your "/" root and "/home" you can use ext3 without any issues.

---

### Post by Viral on 2006-08-21
Uh oh.

While nobody responded, I decided to go ahead and just try it. Bad idea. In the process of installing, the window came up asking me for the partion stuff. I manually did it, and wow, huge mistake.

Here is what I did:

- HD 60 GIG

First, I freed up as much space as I could on windows. I put in the live cd, rebooted, and got onto the desktop of Ubuntu. On the desktop, it said: "Install" or whatever, so I clicked it. Now, it asked me the usual questions, until I got to the Partioning part. I clicked the third option, and it loaded up the manual thing. I wish I could take a screenshot to show you...

Anyway, I must have messed up because once it finished, I thought I messed up because it only had 3 drives that asked me to choose the mapping, so I clicked "Back", and all the drives had "corrupted" or something on them, and so it gave me an error, and it turned off my computer.

I turned it back on, and it said: No OS found.

!!!!!!!!!!

Good thing I have Windows and all my files backed up. I installed Windows once more, and then tried installing Linux once again, same problem. Same thing. I'm installing Windows AGAIN as we speak, so I'm asking for emergency help.

Please, can someone give me a step by step for partioning a 60 gig HD, into 3 sections (Windows, Media/Files, Linux) and deul boot. 

Please, I'm desperate here.

Thanks, I'll try to look as soon as I can.

---

### Post by bombitmd on 2006-08-21
Hey Viral!  I just installed Ubuntu 5.04 last night successfully. I'm from the Philippines so the newer Ubunt will take a couple of months to get to me. I had 5.04 delievered a long time ago but never knew how to use it.  I am an absolute beginner too, so I know exactly what you're going thru.

I found this site [http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/")
very very useful. It's how I learned to dual boot my XP.

I'll describe how I did it, step by step. Hopefully you can follow suit, applyiing what you can.  I have an old computer (8GB HD only). I used Partition Magic for partitioning, but you can use GParted from the Ubuntu Live CD (more on this later.)

So, let's start:
1. Backed up all files on a CD-R.
2. Booted from my XP installer and began re-installing XP to fill up my entire drive.
3. After XP was installed, I installed Partition Magic to begin partitioning.  Alternatively, after XP install, you can reboot and boot with LiveCD to start Ubuntu. There you can run Gparted under System (I think.) Since you have your partitioning mapped out, here's the next step:
4. Partitioning (using PartitionMagic or GParted):
  a. [COLOR="Blue"]Resized [/COLOR]C: (where Windows XP is)drive to desired size
  b. [COLOR="Blue"]Created new partition[/COLOR] with desired size for my Windows personal files as [COLOR="Red"]FAT32[/COLOR]
  c. [COLOR="Blue"]Created new partition[/COLOR] w/ desired size for **[COLOR="Red"]/home[/COLOR]** directory. Set as [COLOR="Red"]logical [/COLOR]and use [COLOR="Red"]ext3[/COLOR] file system.
  d. [COLOR="Blue"]Created new partition with desired size[/COLOR] for [COLOR="Red"]swap [/COLOR]directory. Set as [COLOR="Red"]swap-linux[/COLOR] and as [COLOR="Red"]logical [/COLOR]drive.
  e. [COLOR="Blue"]Created new partition[/COLOR] w/ [COLOR="Lime"]remaining space [/COLOR]for root directory. Set as [COLOR="Red"]primary[/COLOR], and [COLOR="Red"]**make bootable**[/COLOR]. (Make sure you get these settings right.)
  f. Apply these partition changes.

5. When I was done, the computer rebooted. I started XP first to check if the drives for C: and D: were done right. They were, so I rebooted, this time I booted with Ubuntu installer in CD ROM.

6. Installing Ubuntu
  a. When Ubuntu starts, choose [COLOR="Red"]default [/COLOR]installation. Choose your settings until you get to Partitioning (again). 
  b. There should appear in its list, 5 partitions. The fist 2 for WinXP (NTSF)and your windows files (FAT32).
  c. Next would be the three Linux partitions: /home, swap, and / (root). 
  d. Choose each one by pressing ENTER and make sure that they are set properly:
       /home = mounted as /home, using ext3 file system, logical drive
       swap  = mounted as swap
       /     = mounted as /-root, using ext3 file system, primary drive, AND           
BOOTABLE
  e. NOTE WHICH PARTITION THE root IS IN. If there's a #3 before it, it means it's in the 3rd partition.

7. Finish partitioning and continue with the installation.

8. Again, create your settings as appropriate to you, and create your user account and passwords.

9. GRUB loader
  a. When you get to the Grub loader, DO NOT write over the Master Boot Record.  Choose [COLOR="Red"]NO [/COLOR]when it asks. 
  b.  It will then ask you where top put it. Place it in [COLOR="Blue"]/dev/hda3[/COLOR] (or whichever partition Linux root is in, the number in hda being the partition number.) 

10. After that, you just let the installation finish and soon you'll be running Ubuntu!

Good luck and have fun with Ubunutu!  I'm still learning the ropes.  Now I'm going to figure out how to share a common drive so I can access files from my Linux system from Windows, and vice versa.

Good luck!

---

### Post by bombitmd on 2006-08-21
Forgot to mention:

When you're installing Ubuntu and you get to the partitioning part, choose [COLOR="Red"]**EDIT PARTITION MANUALLY**[/COLOR]. Then edit the Linux partitions as I described above.

---

### Post by confused57 on 2006-08-21
If you use the alternate cd to install, see this guide:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

There's some excellent screenshots and explains about partitioning.

Here's a link for using gparted to partition, hope it isn't too confusing...but it gives some excellent screenshots and tutorials:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

First, get Windows installed and working, then post a reply before trying to install Linux again.
Look back over the link for installing with the Live CD given earlier:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
Go down toward the bottom of the page and read over the section for manual partitioning option, especially setting up the root(/)  & swap partitions and setting up a "Documents" partition(mount point) that can be shared between Windows & Ubuntu.

---

### Post by H.E. Pennypacker on 2006-08-22
> 
Here is what I want:

Out of a 60 gig HD:
- 7 gigs for Windows
- 7 gigs for Linux (ubuntu)
- 7 gigs for Backup (came with my gateway...)
- 39 gigs for everything else (CAT32) so I can exchange media between the two.

Good idea? What are your opinions?

There is no need to create a partition simply for sharing files between two or more operating systems.  Here is what I recommend:

Windows - 5GB
Ubuntu (root directory) - 10GB
Ubuntu (home directory) - 38GB
Swap - Double the size of your RAM.
Backup - Whatever size it needs to be (I assume its 7GB).

There is no particular reason I went with these numbers.  These numbers are commended, and as a new Linux users, I suggest you go with these numbers until you get a good understanding of everything and know why you may want other numbers.

> EDIT: How do I format my HD that has Windows on it?

WARNING: Formatting your Windows partition will result in disastrous consequences for that partition.  Do this only if you no longer care about Windows.  If you no longer care about your Windows installation, I suggest you remove it entirely using gParted.  Please read about gParted on how to do this the right way.

> Yes, I understand. Why can't I just use FAT32?

Do NOT use Fat32.  First of all, its owned/created by Microsoft.  Second, there's no reason for using it.  Use ext2 or ext3 (I prefer ext3).

> 
After I format my windows drive, and get all my partioning done, what do I do? Exit out of Ubuntu, and try installing Windows?

I personally recommend taking care of all partitioning before anything.  Again, before anything including inserting the Live CD.  Download gParted, burn it, and do all partitioning.  When completely done, start Live CD, and   install Ubuntu.  You won't have to partition again, because you've already done it.

I was able to skip the partitioning part using DiskDrake (don't read about DiskDrake and what it is, because there's no reason for you to know more than you need to know - you will only confuse yourself more) with my PCLinuxOS installation, and I am not sure this can also be done with Ubuntu.


> Anyway, I must have messed up because once it finished, I thought I messed up because it only had 3 drives that asked me to choose the mapping, so I clicked "Back", and all the drives had "corrupted" or something on them, and so it gave me an error, and it turned off my computer.

I turned it back on, and it said: No OS found.

Viral, to be honest, you've obviously done something you should not have done, because what you're describing is highly unusual, and could not possibly have occured if you followed the instructions I linked to on the first page.

I always suggest that people, before doing anything final, first go through several "practice" installations.  You go to through all steps, except the last one, which submits the installation.  You want to try everything a few times before committing yourself to something.  You will become more comfortable, and things will begin to make more sense.  That's how I know what I know now.

---

### Post by A_608 on 2006-08-22
Be sure to choose the create from image option when you burn the iso file. The first time I did not and Unbutu did not start. Also when the partition program loads up you have to make sure there are at least three partitions. I think you know this. I almost forgot to make the third. Are you using the live CD? I read some stuff about the alternate version. From your configuration, you have plenty of ram to run the live CD. On my PC, I reformatted my drive, reinstalled windows, defragmented ,then ran the live CD. It worked. Before I go on, I need to know if you are using the live CD.

---

### Post by Viral on 2006-08-22
Wow, this is really tiring. I blame myself, but I'm not going to give up, after all this trouble.

Well, I'm starting clean. I formated my whole drive with Windows. Right now, I have a clean slate of Windows on a whole drive.

Now, I was recommended to download a program to partion my HD before I got onto Linux. I think that would be better, since I'm more used to Windows then Linux.

The only problem is, the clean slate of Windows is too clean. I have a wireless card, and I can't access the internet because I have no idea how to get it to recognize it. When I go to "install hardware", it asks me to insert the CD of the drivers. Now, how stupid is that? My computer didn't come with any CD's (besides Windows) so I'm pretty much screwed there. I can't access the internet (ethernet or windows) because Windows doesn't have either of those drivers installed. Which means I can't download the program, which means I can't partion my hd. I don't want to do it in Ubuntu due to prevous experiences.

None of my other computers have CD burners.

*Sigh*, please don't think I don't know much about computers, because honestly, I do, but I've never reinstalled Windows, simply because I didn't have a need.

If someone out there could help me out, and end my misery, that would be perfect.

---

### Post by bombitmd on 2006-08-22
Since you can't connect to the Internet, but you have Windows installed and I'm assuming you have the Ubuntu LiveCD, you can try the method I described by booting with LiveCD and use its GParter partitioner. Just follow the steps I gave above (or click on the link I included).  I did this and now I'm dual booting; it worked for me. ;) Good luck!

---

### Post by Viral on 2006-08-22
Ok, I'm trying once more.

Last night I got Windows istalled, although I'm still confused on lots of things, internet, connections, drivers....

anyway.

I'm using the guides that you gyys have given me, I hope I don't screw anyting up, and if I do, well. dumb me ;)

Thanks for the support everyone.

---

### Post by Viral on 2006-08-22
Ok, i'm right in the middle of partioning, and I'm following bombipm's guide, but I don't have internet access so I'm using the one on the installion live cd. Now, when I create a new partion, it won't let me choose Logical. I don't know why, but I can't select it. It won't let me

it's either Primary or Extended.

Problem?

I'm not oging any furter, just in case. Please respond. Thanks!

---

### Post by Maylar on 2006-08-22
Pick Extended. It will create the logical partition for you. You can only have 4 Primary partitions. However, an Extended Partition will create the Logical partition. Which would count as 1 of the Primary partitions. Think of a Logical Partition as a virtual hard drive. Where it will allow you to create more partitions than the 4 partition limit.

---

### Post by H.E. Pennypacker on 2006-08-23
Viral, you'll have to get used to Ubuntu at some point, so go ahead and use gParted to do all the partitioning.   Start up the Ubuntu LiveCD, and if it doesn't come with gParted, download it.  Then start gParted, play around with it before finalizing anything, and once you're comfortable,  start partitioning.

This will be a lot easier than worrying about all your Windows troubles, and setting up this and that.  Knowing how to use gParted could solve many headaches.

You should create *one* extended partition for Ubuntu.  This partition will then allow you to create logical ("sub-partitions") partitions.  After creating an extended partition, inside of the extended partition, create three logical partitions.  One for root, one for home, and one for swap.

Make sure to make use of the guide I provided in my first post.  Check out the first page of this thread.

---

