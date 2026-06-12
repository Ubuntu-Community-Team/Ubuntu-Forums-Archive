---
title: "Can someone proof read my dubious triple boot partition scheme please?"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by Seaniesean on 2008-11-10
Hello, I'm just about to repartition my macbook to have OSX, XP, Ubuntu, and a data partition.  I know there are many, many guides to this, I'd just like someone to have a little look.  My current plan is as follows...

partition 1- EFI 200mb thingy
partition 2- FAT32 Data partition
partition 3- EXT 2 Ubuntu/GRUB
partition 4- NTFS Windows XP
partition 5- HFS+ OSX
partition 6- Linux swap

I think that'll work, am I right?

So, here's the plan.  Stick the OSX DVD into the macbook, use disk utility to create the partitions, install OSX, install Refit, install windows XP, install Ubuntu and GRUB, all done.

And here are some questions...

What partitions should I create with the disk utility?  I know I can make HFS, FAT32 and "linux" partitions.  I also notice that disk utility can create a "swap" partition.  Is this a linux swap partition, or something else?  So basically, can I make the swap partition with OSX, or should I use Gparted or something to do this?

Also, can I forget the swap partition and just make a swap file on the linux partition?  Is this a good idea, or not really?

Finally, if I don't use boot camp for any of this, would there be problems?  I mean, is there any special functionality in boot camp besides resizing a disk and creating partitions?  I suppose my question is what does boot camp actually do, and do I need it to do what I want?

I'm pretty sure I had more questions than that.  Ah well.  Any help or comments are greatly appreciated!

---

### Post by Tu1J4kXk8NUhMz on 2008-11-10
#1 - Will it work?
Yup, it should. However, you might run into problems having Mac OS X as the final partition. I don't know that for sure, just something I've read from time to time. Oh, and also, if you're installing GRUB in the Ubuntu partition (which is the best way to go anyway, FYI), you don't need a Linux swap partition.

#2 - How to create partitions...
How I did it was to create "placeholder" partitions. FAT32 is ok to be handled by Disk Utility, as well as HFS+ (of course). However, I've had problems with Disk Utility working with ext2/3 as well as NTFS. Let the Windows install disc switch your one partition to NTFS. 
As for the Linux partition, just create an HFS+ partition and name it "LINUX", then when you install Ubuntu, delete that partition and recreate it as ext2/3 (whichever you want).

#3 - Whoops! Already answered this, didn't I? GRUB is the only real thing you have to worry about. Don't worry about the Swap Partition.

#4 - Boot Camp
Boot Camp don't do nothing special. You can use it if you like, however it's main purpose is to streamline the Windows install process. Basically what it does is make two partitions out of one, or reverse the process. If you have more than one partition, or if your Mac partition isn't the only partition, then forget it. Boot Camp gets confused.

On a related note, the Boot Camp loader is pretty much ineffective once you change your partition scheme to anything other than [Partition1 - Mac; Partition2 - Windows]. It expects Mac to be the first partition, and if it doesn't find Windows in the second partition, it says there's no operating system. 

Hope that all helped.

---

### Post by cyberdork33 on 2008-11-10
> **teamjh14 said:**
> if you're installing GRUB in the Ubuntu partition (which is the best way to go anyway, FYI), you don't need a Linux swap partition.
For a triple-boot, you will want to install GRUB to the Ubuntu root partition unless you want to have to use GRUB to boot windows (not recommended).

As far as the swap, you can create a swap partition or a swap file no matter your configuration. It is just a preference. I am unsure if hibernation will work properly with a swapfile though...

> **teamjh14 said:**
> #2 - How to create partitions...
How I did it was to create "placeholder" partitions. FAT32 is ok to be handled by Disk Utility, as well as HFS+ (of course). However, I've had problems with Disk Utility working with ext2/3 as well as NTFS. Let the Windows install disc switch your one partition to NTFS. 
As for the Linux partition, just create an HFS+ partition and name it "LINUX", then when you install Ubuntu, delete that partition and recreate it as ext2/3 (whichever you want).

My suggestion would be to use Disk Utility to partition something like this:
1. EFI
2. Big FAT32 partition to hold space
3. OSX
4. small partition for swap if you decide to keep it as a partition.

Then boot into gparted and shrink the FAT32 to the size you want for storage and create your Windows and Ubuntu partitions in the free space left after resizing. After that, make sure that the partition tables are all in sync and go for the rest of the isntalls.

> **teamjh14 said:**
> #3 - Whoops! Already answered this, didn't I? GRUB is the only real thing you have to worry about. Don't worry about the Swap Partition.
GRUB and the swap partition really have nothing to do with each other... I don't understand this logic... ? I prefer a swap partition, but it is really just what you prefer.

> **teamjh14 said:**
> #4 - Boot Camp
Boot Camp don't do nothing special. You can use it if you like, however it's main purpose is to streamline the Windows install process. Basically what it does is make two partitions out of one, or reverse the process. If you have more than one partition, or if your Mac partition isn't the only partition, then forget it. Boot Camp gets confused.

On a related note, the Boot Camp loader is pretty much ineffective once you change your partition scheme to anything other than [Partition1 - Mac; Partition2 - Windows]. It expects Mac to be the first partition, and if it doesn't find Windows in the second partition, it says there's no operating system. 
Yep. You can essentially ignore BootCamp if you just use DiskUtlity to do the initial partitioning.

---

### Post by Seaniesean on 2008-11-10
This forum is brilliant.  So, the only thing I wonder about is teamjh14's comment that OSX doesn't like being at the end?  I thought it had to go at near the end because Windows or Linux can't boot from beyond partition 4, but OSX can.  Will putting a swap partition at the end make OSX feel better?

Also, for the swap partition, should I just leave it unformatted with disk utility and format it as linux swap with gparted, or leave it to the ubuntu installation process?

I quite like cyberdork33's suggestion to format one big FAT partition and then convert to NTFS/EXT.  I believe I shall do that.

Thank you very much for your inputs, it sounds like it should be quite easy but I like to check because I do screw things up from time to time.

---

### Post by Tu1J4kXk8NUhMz on 2008-11-10
> **cyberdork33 said:**
> 

GRUB and the swap partition really have nothing to do with each other... I don't understand this logic... ? I prefer a swap partition, but it is really just what you prefer.


DO NOT QUESTION ME! :-P In all seriousness, I was under the impression that the swap partition was specifically for GRUB. You would easily know better than me though.

> **Seaniesean said:**
> This forum is brilliant.  So, the only thing I wonder about is teamjh14's comment that OSX doesn't like being at the end?  I thought it had to go at near the end because Windows or Linux can't boot from beyond partition 4, but OSX can.  Will putting a swap partition at the end make OSX feel better?

That could be entirely possible, as my configuration doesn't go past Partition 4. I'm not even sure that Mac cares, as I have my OSX partition right at the beginning. Just passing on what I'd heard from a select few. I am far from an expert, just pulling from my own experience.

Good luck, man!

---

### Post by cyberdork33 on 2008-11-10
> **Seaniesean said:**
> This forum is brilliant.  So, the only thing I wonder about is teamjh14's comment that OSX doesn't like being at the end?  I thought it had to go at near the end because Windows or Linux can't boot from beyond partition 4, but OSX can.  Will putting a swap partition at the end make OSX feel better?
I think it will be OK. I had both Tiger and Leopard installed when Leopard first came out and it was installed in partition 5 like that... It worked fine.

> **Seaniesean said:**
> Also, for the swap partition, should I just leave it unformatted with disk utility and format it as linux swap with gparted, or leave it to the ubuntu installation process?I would use gparted for that, but that is just because I do not trust DiskUtility to make a proper Linux partition. :)

---

### Post by cyberdork33 on 2008-11-10
> **teamjh14 said:**
> DO NOT QUESTION ME! :-P In all seriousness, I was under the impression that the swap partition was specifically for GRUB. You would easily know better than me though.
just think of swap as disk space that can be used like RAM. Most modern desktop-use machines could probably get away with not having any swap at all, but you do need swap for hibernate (as the contents of RAM gets dumped there before power-down).

---

### Post by Tu1J4kXk8NUhMz on 2008-11-10
> **cyberdork33 said:**
> just think of swap as disk space that can be used like RAM. Most modern desktop-use machines could probably get away with not having any swap at all, but you do need swap for hibernate (as the contents of RAM gets dumped there before power-down).

You mean like virtual memory for Windows? Well, that makes a good deal of sense. Thanks for straightening me out, BTW. You are always so helpful for me!

---

### Post by Seaniesean on 2008-11-10
Yeah, that sounds good to me.  I think I'll go with a swap partition on the end, and make it with gparted, along with the EXT2 and NTFS partitions.

Have either of you triple booting dudes found a good way to make a restorable clone or image of the entire triple boot setup?  Someone told me about something called "hard disk copy" the other day, though I have not tried it yet.

---

### Post by cyberdork33 on 2008-11-10
> **Seaniesean said:**
> Yeah, that sounds good to me.  I think I'll go with a swap partition on the end, and make it with gparted, along with the EXT2 and NTFS partitions.

Have either of you triple booting dudes found a good way to make a restorable clone or image of the entire triple boot setup?  Someone told me about something called "hard disk copy" the other day, though I have not tried it yet.

you could technically use dd on the entire disc, but that would literally clone it to somewhere else.

---

### Post by Tu1J4kXk8NUhMz on 2008-11-11
No clue, man. I tend to backup each partition separately in Mac OS X, using Time Machine for Mac and Winclone for Windows (don't have a good solution there for Ubuntu, though).

In doing a Google search, I have yet to find a backup program that will do what you're looking for, unless you do an absolute clone like what Cyber is talking about.

---

### Post by Seaniesean on 2008-11-11
Someone else suggested dd the whole disk last time I asked about this.  Hmm.  What, and then boot from live CD and dd the whole disk back again to restore, yes?  I suppose I could do that, but then if the HD is 160G then the backup will be the same size, am i right?

Using three different methods for each OS is a bit messy, but a combo of superduper for OSX, winclone, ghost or umpteen others for windows, and tar for ubuntu sounds quite good.  At least they are compressed a bit.  

If I could program, I'd make a program that could create an image of all the partitions I want and restore it from an external drive using a boot cd.  I'm quite surprised such a thing doesn't exist actually (as far as I can tell).

Well, thanks again!

---

### Post by And6ate9 on 2008-11-18
I have a question. How can you use the installer to install grub on the linux partition?

Also I am interesting in doing a triple boot XP, ubuntu, ununtu studio is it possible to have 2 swap partitions for each linux distro?

---

### Post by cyberdork33 on 2008-11-19
> **And6ate9 said:**
> I have a question. How can you use the installer to install grub on the linux partition?just boot the livecd, open a terminal, and run 'sudo grub' and you are at the grub prompt where you can install grub manually. See instructions here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

> **And6ate9 said:**
> Also I am interesting in doing a triple boot XP, ubuntu, ununtu studio is it possible to have 2 swap partitions for each linux distro?
Yes you can, but it isn't needed. You can use the same swap partition for both installs.

---

### Post by Seaniesean on 2008-11-21
Hmm.  Well, I got <something> up and running, but not quite how I'd like.  I think it went something like this...

Created "3" partition scheme with OSX install disk with bonus EFI partition so it goes EFI, FAT, HFS+, Swap.

Turned FAT partition into 3 partition scheme with GParted and created better swap partition at the end so now it goes 
EFI, FAT, NTFS, EXT3, HFS+, Swap.

Install OSX no problems.

Tried to install Windows...Windows only sees EFI, FAT, HFS+ and Swap partitions, not the NTFS or Linux partitions.  It calls the NTFS and Linux partitions free space. (Doesn't like more than four partitions?!)

Tried creating other partition schemes, but I really couldn't get windows to install where there are more than four partitions on the disk or by trying to get the XP install CD to create a fifth partition.

So, what's the trick?

In the end I just did a standard three partition scheme with OSX so it goes OSX, Linux, Windows, with a swap file for Ubuntu, not a swap partition.  So I don't have a data partition, which is a pity.

Anyway, I have some random questions if you please...

The fans seem busier in Ubuntu than OSX.  Is this normal?  What should I do about it?  

I have data transfer between OS's partially solved.  

OSX sees windows

Ubuntu sees OSX and Windows and can write to windows

Windows sees OSX and Ubuntu and can write to both (I think)

So, I heard if you disable journaling in OSX, Ubuntu can write to it.  Any terrible consequences of disabling journaling in OSX that I should be aware of?

I can't get OSX to mount EXT3.  I tried Macfuse with some ancient driver that didn't work.  Any other ideas? 

In Ubuntu, my mouse clicks are doing some crazy stuff.  Like, when I right click a hyperlink in firefox it does other stuff besides bring up the normal "open in new tab" etc. rollout like try and compose an email.  I presume there is some sort of mouse sequence that initiates this?

Finally, what's the best way to set up two independent-ish desktops using the notebook and an external monitor on a macbook with Ubuntu?  I believe it is a second generation (2,1) macbook with intel integrated GMA graphics.  I saw something called Twinview but I believe that's for NVIDIA cards.  I just want to be able to use two screens independently (with different apps. etc. on each screen like the multiple workspaces but on two monitors)

Think that'll do for now.  

Thanks!

---

