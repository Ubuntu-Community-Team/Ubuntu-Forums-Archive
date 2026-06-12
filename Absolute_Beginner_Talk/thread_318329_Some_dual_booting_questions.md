---
title: "Some dual booting questions"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2006-12-13
Hi! My name's Adam and I've been testing out 6.06 with the LiveCD for a while now and I have some questions about partitioning and dual booting. These have probably been asked hundreds of times, sorry. 

My setup:
Dell Inspiron 4150
XP Pro SP 2
28GB hard drive (15.4GB of which is free space)
1.7GHz CPU, 640MB RAM

First, Is it advisable for me to purchase a 20 to 30 GB external drive and install Ubuntu on that? Is that safer than partitioning? I can get a pretty cheap one from NewEgg so price is no big deal.

Or is my 28GB hard drive more than enough space for both XP and Ubuntu? I don't do heavy video editing or anything like that, but it would be nice to have some space in reserve.

Third, if I do decide to partition, it seems like I need to create some "swap" space, according to [_this guide_]("https://help.ubuntu.com/community/WindowsDualBoot"). What does that mean and why?

Lastly, what are the advantages of manual partitioning (the third installation option) versus letting Ubuntu do it for me by resizing the XP partition (the first installation option)? I'd prefer not to totally erase my XP partition, so the second option is out for now.

Thanks a ton for your help everyone!

---

### Post by pay on 2006-12-13
Ubuntu can run on a serparte harddrive than Windows or on the same one. I think that the minimum space for ubuntu is 5-6 gb. For swap I would normally go with double my own ram, if possible of if not atleast the same size as the ram. If you decide to manually partition you have more controll over what filesystems you use (ext3 reiserfs (v3) xfs....)

---

### Post by Cabldevil on 2006-12-13
Ubuntu will partition automatic  - it will ask you if you want to change partiton size and use the free disk space.  It wil install grub and allow dual boot with no problem.

You should have enough space  but I would think about a bigger drive  unless your not goint to use the 28gig for mp3s or vid.

External  I would not do at all.  speed will be down and it will not be easy as reg install.  I would save your $$ and get a 120 gig for 30$ on zipfly

---

### Post by bodhi.zazen on 2006-12-13
> **hackle577 said:**
> Hi! My name's Adam and I've been testing out 6.06 with the LiveCD for a while now and I have some questions about partitioning and dual booting. These have probably been asked hundreds of times, sorry. 

First, Is it advisable for me to purchase a 20 to 30 GB external drive and install Ubuntu on that? Is that safer than partitioning? I can get a pretty cheap one from NewEgg so price is no big deal.

You can get a large internal HD or less $$

If you must use an external one make sure it is Linux compatible and your bios can boot it.

> Or is my 28GB hard drive more than enough space for both XP and Ubuntu? I don't do heavy video editing or anything like that, but it would be nice to have some space in reserve.

IMO your 28 Gb drive is too small.

Ubuntu can be done in 6 Gb or a little less, but that leaves little room for those big video files....

> Third, if I do decide to partition, it seems like I need to create some "swap" space, according to [_this guide_]("https://help.ubuntu.com/community/WindowsDualBoot"). What does that mean and why?

I'll skip that one for now.....

> Lastly, what are the advantages of manual partitioning (the third installation option) versus letting Ubuntu do it for me by resizing the XP partition (the first installation option)? I'd prefer not to totally erase my XP partition, so the second option is out for now.

Thanks a ton for your help everyone!

If you re-size you windows partition back up your data and defragment several times first.

Then make it as small as you dare.

Then install Ubuntu and I see no reason to manually edit your partition table at this stage of the game, but that is my advice....

See this guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Qrk on 2006-12-13
I wouldn't bother buying a new hard drive. Ubuntu really only needs about 7 GB for just about everything you could want installed (+data), including Gnome and KDE.

The swap partition is for Linux's version of virtual memory. Both windows and Linux can and do use the hard disk RAM sometimes. Its good to have a swap partition of a couple a hundred MB. (The rule of Thumb used to be twice your RAM, but nowadays people have a ton or RAM so it isn't needed as much)

Manually editing the partition table will bring up gparted, which allows you to make more advanced partitioning schemes. Many people like having their home folder on a separate partition, or making a Fat32 partition for sharing Data between windows and Linux. I wouldn't worry about doing all that though, as Ubuntu's default scheme will help you get all that you need to.

Also, Ubuntu's first option will help you in creating a swap partition of the appropriate size. Letting Ubuntu do it for you is a good option, and it will let you keep XP.

Just remember -- defrag windows first!

---

### Post by gn2 on 2006-12-13
Remember to leave 25% free space on your NTFS partitions or they will struggle to defragment properly.......

---

### Post by hackle577 on 2006-12-13
So if I do partition (which bodhi.zazen doesn't seem to endorse), how small could I make my Windows partition? Right now Windows is taking up 12.4GB on my drive, so should I maybe leave 15GB for Windows and 13GB for Ubuntu? Or am I missing something?

Thanks again. :-)

EDIT: Ok, let me just ask that specifically. Out of 28GB, how much for XP and how much for Ubuntu? Or is that definitely too small? I don't have any large video files, but I do have about 1.3 GB worth of music.

---

### Post by bodhi.zazen on 2006-12-13
> **hackle577 said:**
> So if I do partition (which bodhi.zazen doesn't seem to endorse), how small could I make my Windows partition? Right now Windows is taking up 12.4GB on my drive, so should I maybe leave 15GB for Windows and 13GB for Ubuntu? Or am I missing something?

Thanks again. :-)

EDIT: Ok, let me just ask that specifically. Out of 28GB, how much for XP and how much for Ubuntu? Or is that definitely too small? I don't have any large video files, but I do have about 1.3 GB worth of music.

gn2 has a good point and I would agree it is good to give windows a little breathing room.

I would give:

Windows = 18 Gb

Ubuntu = 10 Gb

Ubuntu will need two partitions, one for / (AKA "root" or the system files themselves) and /swap. Give yourself 1 Gb swap (although you could likely get by with 512 Kb) and 9 Gb for root.

Don't forget to defragment and backup...

HTH 8)

---

### Post by hackle577 on 2006-12-14
Thanks very much! I'll probably be installing soon, so I'll come back if I have any problems.

---

### Post by PWill on 2006-12-14
A little background on why you need swap:
Whenever a program is launched in Linux, the binary and all of the required libraries are moved to the RAM, so that they can respond faster. (This is also why you can update your system without restarting in Linux)
Swap is virtual RAM, stored in a partition on your hard drive. If I were you, I would make a 1.25GB swap partition, since you have a low amount of RAM.
Hope your install goes well! Be sure to let us know.

---

### Post by hackle577 on 2006-12-14
So basically my partition scheme is going to be this:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning2.png[/IMG]

Where the Windows partition is around 17.25 GB, the Ubuntu partition around 9.25 GB, and swap around 1.25 GB. Correct?

Then, if I understand things correctly, I'll come to this screen:

[IMG]http://img153.imageshack.us/img153/2556/w2u310xn.png[/IMG]

My mount points will be swap and root, just like the picture, but what would I put for the mount point of my third partition (Windows)? Also, would I check reformat for any/all of them? I'm guessing "no" for Windows.

Thanks for the help. I can see questions like these popping up constantly on the forums so I know you guys must be sick of them by now. But I've never seen a forum, on any topic, where people responded more quickly and more helpfully than this one. :D

---

### Post by bodhi.zazen on 2006-12-14
I would not make swap larger then 1 Gb.

The size of Windows and Ubuntu sound good, but the picture looks off..... It is fine if the numbers are as you state......

Last mount windows in /media/windows if you want an icon (for the drive) on your desktop or /mnt/windows if you do not. My advice is /mnt/windows but I like a clean desktop.....

You will have to enter the mount point manually.....

Otherwise go for it !

EDIT: Looking at your picture it lists /125 Gb for root. Is this true?

---

### Post by hackle577 on 2006-12-14
Sorry, I probably should have mentioned in my post that those pictures are NOT from my comp. I used pictures from several psychocats.net guides ([_here_]("http://www.psychocats.net/ubuntu/partitioning") and [_here_]("http://www.psychocats.net/ubuntu/installing")) just for a visual reference, probably more for myself than anyone else. I know they are not to scale, especially for my computer. Sorry for the confusion.

Also, what about checking the reformat box? Should I check the ones for my new root and swap partitions, but not the one for Windows?

Anyway, it looks like it's gonna be swap 1 GB, Windows 17.5 GB, and Ubuntu 9.5 GB. I'll probably mount Windows at /mnt/windows (I'm a fan of the clean desktop as well). Beforehand I'll defrag a few times, delete unnecessary programs/files, clean temp folders, etc. I have 2 exams today so I should get around to the actual install at about 7pm EST. I'll let you guys know how it goes and if I have problems.

Thanks!

---

### Post by hackle577 on 2006-12-14
So I finished up today earlier than expected. I'm going to install as soon as I can get this question answered.

About checking the reformat box... should I check the ones for my new root and swap partitions, but not the one for Windows? (See the above post for more details.)

Thanks! :-)

---

### Post by hackle577 on 2006-12-14
Alright, I've backed up my My Documents folder (anything else I might want to keep?). I've also made a lot of room by sifting through my music collection and deleting about half of it. I'm now starting on the first defrag of my hard drive. I should be installing as soon as I get an answer above.

---

### Post by dbd on 2006-12-14
> **hackle577 said:**
> Also, what about checking the reformat box? Should I check the ones for my new root and swap partitions, but not the one for Windows?

Yep, that's exactly it, new partitions must be formatted, and you don't want to format the Windows one or you'd lose your data!

I'd advise you make an extra /home ubuntu partition. So make the / partition 6.5Gb and /home 3Gb. This is because all the custom settings for your user will be stored here, and you can also store some data here. So if for any reason you decide to reinstall you can just format the / partition (keeping /home intact) and then even after a reinstall all your settings will be kept. :)

Good luck, and have fun :D

---

### Post by hackle577 on 2006-12-14
Alright! Install went smoothly except for one error during installation (about 85% of the way in). It said "Cannot access security updates." I'm guessing all I have to do to fix this is manually run an update?

I haven't tried booting into XP yet, so we'll see how that goes in a few minutes. I'd like to say thanks to everyone that helped in this thread, especially bodhi.zazen. Also, thanks to the guys in the Ohio LoCo forum, who couldn't have made a better first impression.

---

### Post by hackle577 on 2006-12-14
Alright I've booted into Windows and it's telling me that "Windows has finished installing new devices. The software that supports your device requires that you restart your computer. You must restart your computer before the new settings will take effect. Do you want to restart now?"

Is this normal? I'm thinking I should reboot but I just wanted to check...

EDIT: Also, my Windows clock is saying that it's 9:05pm, when it is only 4:05pm EST here.

---

### Post by oracle5 on 2006-12-14
Its okay to reboot windows. Its just because your hard drive has changed and windows had to think about it. Mine was the same way when I first dual booted my computer.

oracle5

---

### Post by bodhi.zazen on 2006-12-14
hackle577:

Welcome to Ubuntu !

All is well I trust ?

---

### Post by hackle577 on 2006-12-14
Everything's pretty sweet so far, although I haven't experimented around in-depth yet. I'll probably test out some various tasks tonight to get the feel. Thanks!

---

### Post by gn2 on 2006-12-14
Now you need to read up on Grub editing, and make a "Super Grub Disk" just in case things go wrong during your update.......

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Enjoy Linux, and know you need never pay for any software ever again. :)

---

### Post by louieb on 2006-12-14
> **hackle577 said:**
> EDIT: Also, my Windows clock is saying that it's 9:05pm, when it is only 4:05pm EST here.
The clock switching time when alternating boots between XP and Linux is a pain. To keep Linux from using UTC Right click on the clock > Preferences >   uncheck the UTC box.
or if you don't have the clock edit /etc/default/rcS and change the  line UTC=yes to UTC=no

---

### Post by hackle577 on 2006-12-14
Clock problem fixed.

I downloaded the USB version of Super GRUB Disk, since I can't burn ISO's. I'm reading the readme.txt and it's Greek to me. I think I can figure out what to do, but I don't wanna eff something up this quick. Here are the included instructions:

Mount your usb hd
	# mount /mnt/usb # or whatever it is 
untar file in your usb hd (or copy contents of it to usb hd)
	# tar xvjf file.tar.bz2
	# tar xvzf file.tar.gz
umount your usb hd 
	# cd /
	# umount /mnt/usb
open grub as root 
	$ su
	# grub
	grub> device (hd3) /dev/ubb # my usb device in linux is called /dev/ubb 
	grub> root (hd3,0) 
	grub> setup (hd3) 
	grub> quit 
	# reboot # If you want to try SGD right now.

I'm assuming this is all stuff to enter into the Terminal, but yeah... Thanks!

---

### Post by gn2 on 2006-12-14
Don't worry about the Super Grub Disk, chances are you'll be fine, it's just that on a dual-boot system, if Grub goes wrong it can stop Windows booting.

It's just something you should know about.

---

### Post by hackle577 on 2006-12-14
My Update Manager is not showing any available updates. Any thoughts?

---

### Post by dbd on 2006-12-15
> **hackle577 said:**
> My Update Manager is not showing any available updates. Any thoughts?

You could try running it on the command line to see if it gives you any useful error messages. Run the command:
> sudo aptitude update
followed by:
> sudo aptitude upgrade

---

