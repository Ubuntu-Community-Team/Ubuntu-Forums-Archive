---
title: "Easy to install? NO WAY!!"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by iggypopp on 2008-01-08
Hi,

I've heard so many good things about ubuntu, and want anything but windows. So I downloaded it.. it runs as a live CD, but trying to install it on a run-of-the-mill 160GB IDE HDD.. FAIL!

I get to the 'partitioner' part, click 'Guided, Resize... and use freed space' (the first one)
[COLOR="Red"]Error: An error occurred while writing the changes to the storage devices.[/COLOR]

The resize operation is aborted.

OK, so I try to do it manually:

it shows both of my partitions (NTFS) as 0 bytes used.. whatever.

when I try and install it:
[COLOR="Red"]No root file system is defined.

Please correct this from the partitioning menu.[/COLOR]


arrghh!!

so I choose /

it tells me I can't use the current disk system and recommends EX2. So I click EX2. 
[COLOR="Red"]"You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory.
If you do not go back to the partitioning menu and assign a swap partition, the installation will continue without swap space."[/COLOR]


the live CD is great.. but why does installing it have to be so difficult?

I am using an AMD 3200+, 160GB HDD, 2 NTFS partitions, one which contains windows xp.. very legacy hardware.. so I don't know why there's any problems..

thanks

Russel

---

### Post by SomeGuyDude on 2008-01-08
Choosing a root mount point and making a swap partition is incredibly standard for a Linux installation, actually. I don't know why the Guided method didn't work for you, but there's no reason to blame Ubuntu for correcting you about the mount point and swap space because that's just how Linux works.

---

### Post by benrboone on 2008-01-08
It should work automatically
but it not to hard to do manually ether
Ubuntu needs at least two partitons
I would recommend at least three
first the root partition also known as "/"
second a swap partition 
third (recommended) a home partiton

when I setup ubuntu i create the three partitions then i go back and assign them
depending on disk space I like to have a 4 to 8 gig space for root or "/" .  a swap partiton equal to memory of the computer (I usually just use 1 gig if room is not a issue). and then I like to have a least 25 gig for home

minium spec:
are 2gig for root
swap equal to memory
home of at least 6 gig

also i format both the root and home partions as ex3
swap will take care of itself as soon as you tell ubuntu that it is a swap partion
(meaning that swap is always formatted with the right format by declaring it swap)

good luck if you need further help just ask

---

### Post by jeffus_il on 2008-01-08
I wouldn't try to resize an NTFS partition in Linux, no never!

---

### Post by benrboone on 2008-01-08
It usually doesn't have problems but it certainly is easier to resize a ntfs partition that doesn't have very much data on it

---

### Post by Mysticle31 on 2008-01-08
It's a little different.  You will want to shoot the PC many times, both in number of bullets per instance and number of instances.  It's well worth it though. :popcorn:

At least I did.

---

### Post by jeffus_il on 2008-01-08
> **benrboone said:**
> It usually doesn't have problems but it certainly is easier to resize a ntfs partition that doesn't have very much data on it
True, but until recently the ntfs driver didn't know how to write, for me it's to early for resizing, specially during an install, why look for trouble?

---

### Post by hyper_ch on 2008-01-08
do you have vista on your computer?

---

### Post by mikewhatever on 2008-01-08
A live cd installation is the easiest I've seen so far. As a side note, this forum should have a rant section.

---

### Post by lisati on 2008-01-08
Don't get too alarmed about the potential for problems, the handful of installations I've done (both Windows and *ubuntu) have all required some work to get them to the point where I could be happy with them.

There's  a lot of things which can confound the issue - not just different hardware and software options but different expectations by people who will be using the stuff.

It's a credit to the team that things work as well as they do.

---

### Post by stchman on 2008-01-08
> **iggypopp said:**
> Hi,

I've heard so many good things about ubuntu, and want anything but windows. So I downloaded it.. it runs as a live CD, but trying to install it on a run-of-the-mill 160GB IDE HDD.. FAIL!

I get to the 'partitioner' part, click 'Guided, Resize... and use freed space' (the first one)
[COLOR="Red"]Error: An error occurred while writing the changes to the storage devices.[/COLOR]

The resize operation is aborted.

OK, so I try to do it manually:

it shows both of my partitions (NTFS) as 0 bytes used.. whatever.

when I try and install it:
[COLOR="Red"]No root file system is defined.

Please correct this from the partitioning menu.[/COLOR]


arrghh!!

so I choose /

it tells me I can't use the current disk system and recommends EX2. So I click EX2. 
[COLOR="Red"]"You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory.
If you do not go back to the partitioning menu and assign a swap partition, the installation will continue without swap space."[/COLOR]


the live CD is great.. but why does installing it have to be so difficult?

I am using an AMD 3200+, 160GB HDD, 2 NTFS partitions, one which contains windows xp.. very legacy hardware.. so I don't know why there's any problems..

thanks

Russel

Best method for you to use is to create "Free Space" and tell Ubuntu to use the largest continuous free space.  It will work.  Remember Ubuntu cannot use NTFS and needs to use EXT3.

---

### Post by gary0 on 2008-01-08
If you still have vista or xp on the system, boot into that and run chkdsk -f from the command line. Sounds like you have errors on your disk, get windows to fix it and then try installing Ubuntu again.

Gary.

---

### Post by insane_alien on 2008-01-08
sounds like he tried to resize a heavilly fragmented ntfs partition. i've had that sort of error when i tried to resize a fragmented partition(it was also quite full).

---

### Post by winterfire on 2008-01-08
I'm probably the last person to give advise on Ubuntu but, I had the same problem when i tried to install. The way I worked around it was to wipe out all the partitions using a windows install cd or f-disk( I used the cd). After the partitions are gone, just install Ubuntu. It will see the unpartition space on your drive. Thats the way i did it anyway.:)

---

### Post by schauerlich on 2008-01-08
> **mikewhatever said:**
> As a side note, this forum should have a rant section.

It does - Ubuntu Testimonials and Experiences.

---

### Post by iggypopp on 2008-01-08
I found what the problem was.. a bug in the GUI. Apparently I'd clicked 'forward' and 'back' too often, resulting in about 5 options to partion the disc (instead of the 3, two guided and one manual), 2 of them just said '0'. This screen then froze, I logged out and back in again. No matter how many times I tried it, it wouldn't recognize the discs, hence my frustration. After a reboot, it recognized them no problem. I'm installing now.. getting the following error 8(
[COLOR="Red"]
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/COLOR]

I even did a 'verify written data' when burning the disc.. but i'll try it again.

Thx for the replies and sorry for the rant.. I got this disc free in the mail so I shouldn't be complaining at all!!!

---

### Post by philinux on 2008-01-08
Do it one step at a time and post screen shots if you get stuck and someone will help you.

Just press Print screen and it will take shot and save it to your desktop, even on the live cd.

---

### Post by iggypopp on 2008-01-08
I'm still getting that disc error... did a validation check and it says that one file has an error. But now that it's wiped my XP partition (I thought it would keep it!) I can't use the original ISO to burn a new CD. So I am copying from the old one. Is there a way to skip that one file or download it if it is damaged on the CD? Like I said I did 'verify data' as I was burning the CD, and it was OK.

I burned using Disc At Once, and Finalize Disc. At 4x.

I would install version 6 (silver CD, validation OK) but I think I'd just end up wanting version 7. Is there a quick upgrade from 6 to 7, like an update? Or do I have to do a clean install with 7?

Thx again!

Edit: just read that  I can't go from 6 to 7.. will redownload the ISO and try again.

---

### Post by asmiller-ke6seh on 2008-01-08
Are you trying to keep Window$ on the system? You said you wanted to get rid of Window$. If you are willing to get rid of Window$, then you can tell the Ubuntu installer that you want to use the entire disk.

Otherwise, load up window, do a CHKDSK, and then do a COMPRESS. NOW do the guided installation - and I think you will find that it works (I am assuming that the Free Disk you Got in the Mail was a professionally created Ubuntu disk, and not just someone's downloaded-and-burned-at-home copy).

Also, you might want to look at the New User's Guide, below, in my SIG. It's chock full of all kinds of good information (I didn't write it - I just liked to it 'cause it's so valuable).

---

### Post by ugm6hr on 2008-01-08
> **iggypopp said:**
> I'm still getting that disc error... did a validation check and it says that one file has an error. But now that it's wiped my XP partition (I thought it would keep it!) I can't use the original ISO to burn a new CD. So I am copying from the old one. Is there a way to skip that one file or download it if it is damaged on the CD? Like I said I did 'verify data' as I was burning the CD, and it was OK.

I burned using Disc At Once, and Finalize Disc. At 4x.

I would install version 6 (silver CD, validation OK) but I think I'd just end up wanting version 7. Is there a quick upgrade from 6 to 7, like an update? Or do I have to do a clean install with 7?

Thx again!

Edit: just read that  I can't go from 6 to 7.. will redownload the ISO and try again.

If you have wiped your XP partition, you may as well partition **before** installing anything.

For ease, I would recommend you create an XP partition at the start of the HD, and leave the rest unpartitioned (unused).  You can use the Ubuntu 7.10 Live CD to do this (or GParted LiveCD).

Then install XP in the first partition.  Then install Ubuntu using the "Guided-largest free space" option.  Everything will then just work.

PS: Ensure md5sum is OK on iso before installing anything.

---

### Post by t0p on 2008-01-08
> **mikewhatever said:**
> As a side note, this forum should have a rant section.

Damn straight!! Rant rant rant rant rant!! :)

---

### Post by SunnyRabbiera on 2008-01-08
yeh all installs are a pain in the neck, but ubuntu's installer is pretty basic compared to most.

---

### Post by iggypopp on 2008-01-09
WOW.. color me IMPRESSED

THIS IS INCREDIBLE.. yes I've finally managed to install it after a few problems, the last of which was getting stuck at 82% (searching for 'mirror' endlessly.. unplugged internet and it resumed...) but now it's done I can only say:

THERE IS ZERO REASON FOR SCHOOLS TO CONTINUE TO USE WINDOWS AND PAY MILLIONS PER YEAR FOR THE PRIVILEGE WHEN UBUNTU EXISTS!!! FREEEEEE!!!!

I mean everything is there, everything works pretty well, and what doesn't I'm pretty sure someone is working on making it better.

I will have to continue to dual-boot. There's too many XP-specific apps like for my Wii and DS etc.. but if I was in an office or the admin of a computer room at a school.. no questions about it, save thousands of dollars and the students aren't hooked on M$ for their whole lives.

The only gripe I had was the installation.. but that had more to do with ntfs and partitioning etc than anything else.

What can be done to stop M$'s grip on the PC world?? I showed my brother Ubuntu and he literally didn't believe it was free.. that it was pirated or something. So I think it starts there, people aren't aware that it's REALLY free (not asks you to pay after 30 days) and it does just a good a job as windows.

Anyway, thanks to all developers and people on this forum.. I'm just stunned!
:guitar::guitar::guitar::guitar:

---

### Post by shareMenaPeace on 2008-01-09
Also if you bore dnow check out

linuxmint.com  ....

---

### Post by kpkeerthi on 2008-01-09
> I've finally managed to install it after a few problems, the last of which was getting stuck at 82% (searching for 'mirror' endlessly.. unplugged internet and it resumed...)
Happened to me as well when installing gutsy minimal in virtualbox. I think its bug. It should actually time out when it could not reach the internet.

---

### Post by Paqman on 2008-01-09
> **iggypopp said:**
> 
What can be done to stop M$'s grip on the PC world?? 

In the short-term, nothing. But just enjoy Linux anyway!

---

### Post by philinux on 2008-01-09
> **iggypopp said:**
> WOW.. color me IMPRESSED



Anyway, thanks to all developers and people on this forum.. I'm just stunned!

Glad to here you got it sorted, welcome aboard.

---

### Post by ronmarley1 on 2008-01-09
> **insane_alien said:**
> sounds like he tried to resize a heavilly fragmented ntfs partition. i've had that sort of error when i tried to resize a fragmented partition(it was also quite full).

This is my experience also.  I've found that running defrag in Windows before installing makes things go easier.  Resizing NTFS should  be OK, as long as the Windows OS is XP.  If it's Vista, use Vista's resize tool to create some free space for Ubuntu, then try the install.

---

### Post by bodhi.zazen on 2008-01-09
> **iggypopp said:**
> WOW.. color me IMPRESSED

THIS IS INCREDIBLE.. yes I've finally managed to install it after a few problems, the last of which was getting stuck at 82% (searching for 'mirror' endlessly.. unplugged internet and it resumed...) but now it's done I can only say:

THERE IS ZERO REASON FOR SCHOOLS TO CONTINUE TO USE WINDOWS AND PAY MILLIONS PER YEAR FOR THE PRIVILEGE WHEN UBUNTU EXISTS!!! FREEEEEE!!!!

Welcome. Schools should look at Edubuntu.

Edubuntu = Ubuntu + Education software + Centralized server (data) management.

---

### Post by ronmarley1 on 2008-01-09
> **iggypopp said:**
> WOW.. color me IMPRESSED

THIS IS INCREDIBLE.. 

THERE IS ZERO REASON FOR SCHOOLS TO CONTINUE TO USE WINDOWS AND PAY MILLIONS PER YEAR FOR THE PRIVILEGE WHEN UBUNTU EXISTS!!! FREEEEEE!!!!t it was pirated or somethin

Another convert joins the fold!  I teach high school (English/Language arts) and use Ubuntu almost exclusively on my laptop.  Unfortunately, our gradebook and attendance program work in Windows only.  We us OOo, GIMP, FreeMind, etc... for student workstations, and the PC's in my lab dual boot XP and Gutsy.
Edubuntu is a off-shoot that focuses on schools.
There are many folks (at least in Ohio) using open source tools in education.

PS, Hola, bodhi.  Happy new year!

---

### Post by cmo220 on 2008-01-09
On my vista system, I had to defragment 3 times before I could resize the partition.

---

