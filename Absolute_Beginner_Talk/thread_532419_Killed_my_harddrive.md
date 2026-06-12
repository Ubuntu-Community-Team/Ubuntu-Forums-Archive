---
title: "Killed my harddrive"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-08-22
Today I have done several risky things (like stopping an install, deleting partitions without removing grub etc), and I don't know which one caused it but now I can't prepare the dual boot I was thinking of at the start.

When I put a windows xp cd in, and if a linux is installed, it won't even read the disk and go to linux directly.

When I put a windows xp cd in, and if a linux is not installed, it would give a grub error and won't boot at all.

When I put a windows vista cd in, it installs fine but won't boot with grub errors.

When I put any Linux cd in, it installs AND boots fine,


What I want to do is to first install windows xp and then install ubuntu so I get my dream dual boot. But seems like I am stuck now.


I am not sure how I can fix this. I first thought of replacing grub, but couldn't find any good document on it. Actually I did find a good one but it required me to write a cd and I can't because I am on Ubuntu livecd.

Did this ever happen to anyone? What do you suggest I do?

Thanks a lot.

---

### Post by annda on 2007-08-22
> When I put a windows xp cd in, and if a linux is installed, it won't even read the disk and go to linux directly.

make sure the cd is ok. try to boot from it on a friend's computer if necessary. if you set your computer to boot from cd first and the xp cd is error-free then it should ask you whether you want to install or do something else (i don't remember, it was a long time ago).

p.s. do you have one disk or more? where are the OS's installed and where do you want them installed? i suppose you have GRUB still installed in the MBR but an xp install cd should ignore and overwrite it.

---

### Post by kyphi on 2007-08-22
Seems like you need to alter your boot sequence in the BIOS so that booting takes place from your CD first.

I am not at all clear what you currently have installed and how many hard drives you have and how they are partitioned.

If you had XP installed and Ubuntu and have messed up your GRUB then that can probably be fixed.

Please advise.

---

### Post by Jimmyfj on 2007-08-22
Just out of curiosity, is your drive SATA?

Make sure that your Cd is set at first boot device in your BIOS. Then, when either Windows XP or Vista boots up and you are at the disk partitioning section you may want to delete any existing partitions from there, be sure to let the installer in use write the changes to the disk.

From your description I'd say that you got a faulty XP disk. Just a guess.

---

### Post by Majorix on 2007-08-22
> **annda said:**
> make sure the cd is ok. try to boot from it on a friend's computer if necessary. if you set your computer to boot from cd first and the xp cd is error-free then it should ask you whether you want to install or do something else (i don't remember, it was a long time ago).

p.s. do you have one disk or more? where are the OS's installed and where do you want them installed? i suppose you have GRUB still installed in the MBR but an xp install cd should ignore and overwrite it.

The CD's (I have 2 copies of XP CD's) are ok, I am sure of that because they worked until a few hours ago, And they can't both get scratched at the same time can they?

I have one harddrive. I tried to install from the XP CD with all partitions deleted, with a single partition encoded as NTFS, and I have done some other tries too.

GRUB was working without errors until a few hours ago. Then (I think) after me using GParted LiveCD it started giving errors with Windows CD's. And now it doesn't give any errors, it just says GRUB and sits there indefinitely taking no input.

> **kyphi said:**
> Seems like you need to alter your boot sequence in the BIOS so that booting takes place from your CD first.

I am not at all clear what you currently have installed and how many hard drives you have and how they are partitioned.

If you had XP installed and Ubuntu and have messed up your GRUB then that can probably be fixed.

Please advise.

I checked that I have CD's in the first order so that can't be it/

I had Ubuntu installed running fine until I decided to dual boot today. And no, I don't think it was Ubuntu that messed up my drive.

> Just out of curiosity, is your drive SATA?

Make sure that your Cd is set at first boot device in your BIOS. Then, when either Windows XP or Vista boots up and you are at the disk partitioning section you may want to delete any existing partitions from there, be sure to let the installer in use write the changes to the disk.

From your description I'd say that you got a faulty XP disk. Just a guess.

I think its SATA but never checked. Ubuntu recognizes it as sda1, if that gives a clue.

So what do you say? Should I go and rant at GParted Forums (if they even exist)? :p

---

### Post by por100pre1 on 2007-08-22
Have you considered wiping your HDD? There are some tools available on the web. Hope to see your problem fixed. :-k

---

### Post by Majorix on 2007-08-22
Is there one available for Ubuntu? I googled for it but all that came up was for windows. I can't boot into windows right now.

---

### Post by codejunkie on 2007-08-22
> **Majorix said:**
> Is there one available for Ubuntu? I googled for it but all that came up was for windows. I can't boot into windows right now.
try [dban]("http://dban.sourceforge.net/") download the .iso file and use either gnome baker or k3b to burn the .iso file.

---

### Post by Majorix on 2007-08-22
I can't write any media right now as I am using the livecd. But if there are no other alternatives I will install Ubuntu and then use that program.

---

### Post by por100pre1 on 2007-08-22
I think this could to the trick. Be sure to backup your Ubuntu home files before proceeding, You'll need to reinstall everything if you use this:

[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

EDIT: Being not able to write any media makes this useless. Sorry. :(

---

### Post by Arthur Archnix on 2007-08-22
I know how you feel. I've been there.

Download and burn a gparted live cd. Those things are infinitely useful. Boot to it and delete every partition you see. Save all changes. You know have a brand new hard-drive (or at least it looks that way to the software), congrats!

Now setup a partition for your ntfs drive. However much space you want. You'll need to do some msdos disk label stuff, just go ahead and do it. 

Now put your XP disc in and install. After that, put your ubuntu disc in and install. Tell it to use the free space. Reboot, and enjoy dual boot nirvana.

---

### Post by Aishiko on 2007-08-22
> **por100pre1 said:**
> I think this could to the trick. Be sure to backup your Ubuntu home files before proceeding, You'll need to reinstall everything if you use this:

[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

EDIT: Being not able to write any media makes this useless. Sorry. :(
Woot mad love for the Killdisk program!  Though I'm going to look for shred :)

---

### Post by Majorix on 2007-08-22
> I know how you feel. I've been there.

Download and burn a gparted live cd. Those things are infinitely useful. Boot to it and delete every partition you see. Save all changes. You know have a brand new hard-drive (or at least it looks that way to the software), congrats!

Now setup a partition for your ntfs drive. However much space you want. You'll need to do some msdos disk label stuff, just go ahead and do it.

Now put your XP disc in and install. After that, put your ubuntu disc in and install. Tell it to use the free space. Reboot, and enjoy dual boot nirvana.

GParted is what made this. I am not touching that CD in my life ever again. And it doesn't delete GRUB btw, you might be mistaken there. Thanks for the help though :)

Seeing 2 programs that require me to write them to disk, guess I will install Ubuntu quick. I will still be around as I am on the livecd. God I love being able to surf while installing :D

---

### Post by codejunkie on 2007-08-22
is your windows xp partition still intact and are you just wanting to get rid of grub?
or are you just wanting to wipe the whole drive?

---

### Post by madsmeg on 2007-08-22
I know it seems silly but you haven't answered as to whether you have your CD drive as your first boot device as opposed to your hard drive, if there is no OS on your system it will read the disk next, then when you have an OS on it, it will read the HD first, maybe if you go into BIOS and change the boot sequence you can have an OS installed and still run from disk.

You may have tried it, but its just a suggestion.

Good Luck and let us know how it goes.

Teh Smeg

[EDIT]

my bad didnt see your reply to that one :p only the other 2, nvm then ^^

---

### Post by Arthur Archnix on 2007-08-22
> **Majorix said:**
> GParted is what made this. I am not touching that CD in my life ever again. And it doesn't delete GRUB btw, you might be mistaken there. Thanks for the help though :)

Well, I am sorry that you feel gparted has ruined you life. I believe it's what the ubuntu installer runs though, so if you get it up and running you may need to change your tune ;) And no, I'm not mistaken on the last point. It removes everything. Other than that though, I'm mostly mistaken on everything else.

---

### Post by threeonethree on 2007-08-22
just remove your hard disk and see if you can boot from windows xp cd then?

---

### Post by mrfelker on 2007-08-22
If you re-install Windows you wipe out grub.  In your case this is probably good - when you reinstall Ubuntu and get to the end of the install (try using Alternate install) it will ask you what device to install grub (very unlike the Windows tyrant).  You can either use a seperate boot partition, which I recommend or just a single Ubuntu partition which has everything in it.
Ubuntu will most definitely pickup Windows and make a multiboot.  I don't know what your partitioning scheme is however.  I use a multiboot program BootITNG from Terabyteumlimted - works great for booting in Windows or Ubuntu (MUST have grub installed).  So in short if you boot from a Windows disk and use the recover or fix option it will wipe out GRUB in the MBR - then you can overwrite the MBR with GRUB and boot off the Ubuntu menu.lst.  Have done this many times - never fails.  Windoze first and then Ubuntu (or ANY other Linux distro).

---

### Post by Majorix on 2007-08-23
Ok I used DBAN to wipe the harddisk. The computer is at home now with an (I hope) all-clean harddrive. When I go back home I will try to install XP+Gutsy and let you know how it goes.

---

### Post by por100pre1 on 2007-08-23
> **Majorix said:**
> Ok I used DBAN to wipe the harddisk. The computer is at home now with an (I hope) all-clean harddrive. When I go back home I will try to install XP+Gutsy and let you know how it goes.

*[Fingers crossed]*

---

### Post by Paulmd on 2007-08-23
> **Majorix said:**
> Today I have done several risky things (like stopping an install, deleting partitions without removing grub etc), and I don't know which one caused it but now I can't prepare the dual boot I was thinking of at the start.

When I put a windows xp cd in, and if a linux is installed, it won't even read the disk and go to linux directly.

When I put a windows xp cd in, and if a linux is not installed, it would give a grub error and won't boot at all.

When I put a windows vista cd in, it installs fine but won't boot with grub errors.

When I put any Linux cd in, it installs AND boots fine,


What I want to do is to first install windows xp and then install ubuntu so I get my dream dual boot. But seems like I am stuck now.


I am not sure how I can fix this. I first thought of replacing grub, but couldn't find any good document on it. Actually I did find a good one but it required me to write a cd and I can't because I am on Ubuntu livecd.

Did this ever happen to anyone? What do you suggest I do?

Thanks a lot.

Neither one of those will physically destroy a hard drive. But hard rives die on their own often enough that you might want to check anyway.

Get the hard drive diagnostic tool from the website of the manufacturer of the hard drive. If you don't know who made your hard drive, Seatools from Seagate will do. 

If nothing's wrong physically, you might try nuking the drive. I've found this tool occasionally useful for such. (note: this WILL erase ALL data on your hard drive BEYOND RECOVERY)

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Majorix on 2007-08-25
Sorry for late reply.

I am now on Windows 2000.

You may wonder why not XP? It resists not to work. But Win2000 worked so I am using that for now.

I also have Gutsy Testing on the other partition and it works fine too.

Thanks to everyone for helping me out. Especially por100pre1 for pointing out the possibility of wiping the harddrive.

---

