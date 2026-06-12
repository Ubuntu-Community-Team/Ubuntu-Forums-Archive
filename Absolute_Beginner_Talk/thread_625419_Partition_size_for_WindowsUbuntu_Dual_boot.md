---
title: "Partition size for Windows/Ubuntu Dual boot?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by AggieTwist on 2007-11-28
I have a 120 GB hard drive on my laptop and plan to dual boot Ubuntu 7.10 and Windows XP.  I currently have only 20 GB of free space left and was wondering how much i'll need for Ubuntu and how much I need to leave for Windows.  I can make more space if need be, but am hoping this will be enough.  Also, while running the LiveCD my windows hard drive shows up in Ubuntu so does that mean i will be able to still access files from Windows while in Ubuntu?  I also have a 250 GB Western Digital External HDD that I keep alot of media on, since it shows up on both I assume I can use that as a shared drive...is that assumption correct? Thanks in advance!

---

### Post by siciliancasanova on 2007-11-28
This will shed some light on planning partitions: [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

You will be able to take files from Windows to Ubuntu but not the other way around without doing some modifications first.  For the external it depends on how it's formatted.  If it's FAT then you can share both ways.

---

### Post by jimrz on 2007-11-28
if you are planning to use gusy 7.10 (definitely recommended over previous versions), it can both read and write to ntfs (where previously you could only read ntfs  from ubuntu) so, yes you would be able to use files on your win partition.

By  20Gb free do you mean unallocated or just not used?

if unallocted then ...

Since, I assume, you are not planning on keeping a lot of your data on the ubuntu partition(s) 20 Gb will be more than plenty. I would recommend, also, creating a separate /home partition when you do your install as this wil make life easier should you ever decide or have to re-install. Be awarae that you can have only 4 primary partitions (one of which can be an "extended" partition) on a single drive and therefore, since your laptop almost certainly has some sort of restore partition from the OEM, you will need to use your 20 Gb unallocated space to create an extended partition and then create your "/", "/home" and "swap" (should = 1.5 times the amount of ram in the laptop) partitions within the new "extended" partition, which can contain many "logical"  partitions.

if just unused, then you will need to re-size the partion that it is in and then proceed as above.

---

### Post by AggieTwist on 2007-11-28
okay, so here's my scenario and tell me what you suggest...I read that Gutsy takes 4 GB for installation so I need at least that in my partition.  My external is FAT formatted so I should be able to read and write any files to or from there instead of creating a FAT32 shared partition.  I also read that the "swap" partition should be twice the RAM so that would be 3 GB as I have 1.5 gigs of RAM.  So how large does the /home partition need to be and since I've never partitioned before, i was wondering how straightforward Ubuntu's partition manager is and what steps I will need to take to do all of this.  I am in no rush to dual boot since i'm still using the LiveCD anyway, just planning ahead.  If you could just outline briefly the steps I would need to take and how large you would recommend making each partition...Thanks to both of you!

---

### Post by siciliancasanova on 2007-11-28
Use gParted Live CD  to do your partitioning.  That's my recommendation.

---

### Post by schauerlich on 2007-11-28
> **AggieTwist said:**
> okay, so here's my scenario and tell me what you suggest...I read that Gutsy takes 4 GB for installation so I need at least that in my partition.  My external is FAT formatted so I should be able to read and write any files to or from there instead of creating a FAT32 shared partition.  I also read that the "swap" partition should be twice the RAM so that would be 3 GB as I have 1.5 gigs of RAM.  So how large does the /home partition need to be and since I've never partitioned before, i was wondering how straightforward Ubuntu's partition manager is and what steps I will need to take to do all of this.  I am in no rush to dual boot since i'm still using the LiveCD anyway, just planning ahead.  If you could just outline briefly the steps I would need to take and how large you would recommend making each partition...Thanks to both of you!

You currently have: ```
|-------------100gb ntfs--------------| |--------20gb free--------|
``` And you want ```
|-------------100gb ntfs--------------| |--/--| |----/home----| |-swap-|
``` Right?

In that case, from gparted, select the 20gb free space and make a 6gb ext3 partition mounted as "/". Then select the 14gb free space and create a 11gb ext3 partition mounted as "/home". Then select the remaining 3gb of free space and make a 3gb swap partition mounted as "swap". That should take care of it.

---

### Post by AggieTwist on 2007-11-28
Thanks guys, that should pretty much solve it. Still have alot to learn about Ubuntu but at least now I am ready for my install...Your help was invaluable.

---

### Post by oeolycus on 2007-11-28
Here's my recommendation for 20 gigs.

**[SIZE="2"]Defrag HD in Windows FIRST![/SIZE]**

[LIST]
[*]Boot up Ubuntu 7.10 live cd. [*]Open GParted (under Administration menu). [*]Shrink the NTFS partition down by 20 gigs.[*]Make a new partition from that space that is ext3*[*]Make a swap of about 1-2 gigs (I've had both and don't *really* notice a difference. You'll have to dedicate it as swap, not ext3[*]Finally, make sure the NTFS partition is still flagged "boot"[*]Close GParted.
[/LIST]

Now start the installer, select manual partitioning.

[LIST]
[*]You should see your partitions.[*]Leave NTFS alone[*]Denote the ext3 partition as /[/list]

*with 20 gigs, I think a /home and a /root are a bit irrelevant. If you had more space, I'd say go for it, but with the chance that you might run out of space...it's just not worth it to me.

That should be it. I'm doing this from memory though. GParted is very easy to use, IMO. Make sure all drives are unmounted and you're set to go. I've blown away the "boot" flag before though and not been able to boot (BIOS couldn't find the boot sector) so beware that mistake. After you install Ubuntu, you'll have to edit the GRUB in order to make Windows a bootable option, but there are guides for that and it's not hard if you follow them step by step.

---

### Post by AggieTwist on 2007-11-28
Theoretically, if I were to have more than 20 GB, how much are you talking about?  What do I need more than 20 GB for anyway since all files will be saved on my external shared drive?  Also, could you link to one of those articles you refer to about editing the GRUB?  I still may go ahead and make a separate root and home partition.  I may clear some more room on my hard drive before I do the install and based off of that I may end up with a larger partition area as well.  After the install is complete, how does dual-booting actually work? how do I choose which OS to start up with and how do I switch to the other later?

EDIT: I've managed to free up 32 gigs before defragging and could probably get another 4 - 8 gigs free if I really wanted to but thats about it.

---

### Post by natehatewindows on 2007-11-28
you should be fine with a 2GB swap.   I would make your root 8-10 GB and your /home 15-20GB. 
As far as grub ubuntu will do it all automatic when you install. After the install (and everytime after) when you turn on your computer you will get a menu asking what OS you want to start. its very simple and very effective.

You should defrage you HD in windows 2 or 3 times before shirnking it, this will eleminate all the fragments so the disk is clean. 

if i were you givin you have the extranal i would do:

/ will be 8GB
/home will be 15GB
and swap will be 2GB.

just for your info i have 2GB of RAM and i have a 2 GB swap and it work great. Beofre my first install i read a lot adn found most people say that a swap over 2GB is pointless.

just to make what i said clear about gurb:
Everytime you turn your computer on you will be asked what os you want to boot so to switch to another later you just restart.

The ubuntu partitioner is good, i have used it with no problems many times. 

Also wha kind of notebook do you have? and do you know if you have a restore partition? do you have recovery disks just in case?

also be sure to back up your windows stuff and if i were you i would download Super Grub Disk beofre you install just incase you have any prolems booting. you can google it and burn the .iso to a cd.

good luck and if you need anything else just post it. dont be scared, this process is much esier than it seems once you start. :)

---

### Post by natehatewindows on 2007-11-28
> **oeolycus said:**
> Here's my recommendation for 20 gigs.

**[SIZE="2"]Defrag HD in Windows FIRST![/SIZE]**

[LIST]
[*]Boot up Ubuntu 7.10 live cd. [*]Open GParted (under Administration menu). [*]Shrink the NTFS partition down by 20 gigs.[*]Make a new partition from that space that is ext3*[*]Make a swap of about 1-2 gigs (I've had both and don't *really* notice a difference. You'll have to dedicate it as swap, not ext3[*]Finally, make sure the NTFS partition is still flagged "boot"[*]Close GParted.
[/LIST]

Now start the installer, select manual partitioning.

[LIST]
[*]You should see your partitions.[*]Leave NTFS alone[*]Denote the ext3 partition as /[/list]

*with 20 gigs, I think a /home and a /root are a bit irrelevant. If you had more space, I'd say go for it, but with the chance that you might run out of space...it's just not worth it to me.

That should be it. I'm doing this from memory though. GParted is very easy to use, IMO. Make sure all drives are unmounted and you're set to go. I've blown away the "boot" flag before though and not been able to boot (BIOS couldn't find the boot sector) so beware that mistake. After you install Ubuntu, you'll have to edit the GRUB in order to make Windows a bootable option, but there are guides for that and it's not hard if you follow them step by step.

I think a / and /home is ALWAYS a great idea.

and you should not have to edit the grub menu.lst after the install. if everything goes right ubuntu will know windows is there and add it for you, and i have never had it go wrong in all my installs.

---

### Post by AggieTwist on 2007-11-28
ya, i'm new to this but from everything I've read its basically like having a big "Do-over" button if you screw something up and want to reinstall.  I figure it couldn't hurt anything anyway.

---

### Post by natehatewindows on 2007-11-28
exactly (well pretty much ;) ), and if you dont do it know i am sure you will want to in a month or two. so do you have any more questions?

---

### Post by gn2 on 2007-11-28
> **AggieTwist said:**
> I have a 120 GB hard drive on my laptop .  I currently have only 20 GB of free space left 

In which case if it's "free" space rather than "unallocated" space you need to either start deleting files or buy a much bigger hard drive.

Windows ideally needs 30% free space for effective defragmentation and an absolute minimum of 15% free space.

QUOTE:  [I] It is recommended that you maintain about 30 percent of any NTFS-formatted disk as free space to ensure that you have sufficient room for effective defragmentation. 
[/I]

SOURCE: [http://technet.microsoft.com/en-us/library/Bb742585.aspx](http://technet.microsoft.com/en-us/library/Bb742585.aspx)

XP uses the same defragmenter as W2k

---

### Post by AggieTwist on 2007-11-28
everything you said helps and clears it up quite a bit...  I have a Toshiba Satellite (don't remember model num) and I do have a restore partition that takes up about 12 gigs...I also don't really have that much that I need to worry about backing up and what I do is already backed up since I do it every month or so.  Most of my files are music and video which is replaceable, although it would still be a pain.  So what you are saying is that I don't need to edit the GRUB right?  Probably do the install by the weekend so if I have any more questions or problems I'll post back.

Thanks for that gn2, I know that and am making sure to keep enough room allocated for that.

---

### Post by natehatewindows on 2007-11-28
i also have a satellite :) be careful though, i still dont have sound in gusty because of a bug. 
you should not have to edit the grub. is this space free of unalocated?  if it just empty sapce in windows you mght have some new problems......

---

### Post by AggieTwist on 2007-11-28
i have 48.6 GB free, and was thinking that 20-25 GB of unallocated should work for me and still leave enough for Windows...haven't actually calculated it yet though

---

### Post by natehatewindows on 2007-11-28
yeah that should work. to shirnk windows do this:

start menu>>
right click computer>>select manage

then a window comes up and on the left there should be something like local disk or hard drive (something like that). click it and the in the center of the screen you will see the partitons on your drive. select the one you want to shrink and right click and select "shrink". windows wil not allow you to shirnk it to small, so your safe. be sure to defrage first!  

:)

---

### Post by AggieTwist on 2007-11-28
cool, nice to know...figured i'll defrag 2 or 3 times in a little while....you wouldn't happen to know anything about setting up dialup in Gutsy with a winmodem would you? Right now I'm stuck with dialup til January but being a winmodem it doesn't really wanna work with Ubuntu...have yet to have success with any suggestions. Thanks for everything else!

---

### Post by Sef on 2007-11-28
> Make a swap of about 1-2 gigs

How much ram do you have? 

a) If you have a gigabyte or less of ram, then I would make a 1 gb swap.

b) If you have more than a gigabyte ram then I would skip swap, as a swap would not be needed, unless you are planning on doing heavy gaming or movie making.

---

### Post by vikramsharma on 2007-11-28
> **natehatewindows said:**
> 

You should defrag your HD in windows 2 or 3 times before shrinking it, this will eliminate all the fragments so the disk is clean. 



Defragmentation is a very important process and is most of the time ignored

---

### Post by AggieTwist on 2007-11-28
I have 1.5 gigs of RAM, I do some movie editing occasionally but mostly just music mastering and editing.  Should I still do swap just to be safe or not?

---

### Post by vikramsharma on 2007-11-28
No amount of RAM is enough, video editing requires a lot of RAM have swap size equal to the RAM size (1.5GB) that should be good enough.  More RAM helps in playing movies, would specially be helpful if you are into HD video.

---

### Post by AggieTwist on 2007-11-28
> **natehatewindows said:**
> yeah that should work. to shirnk windows do this:

start menu>>
right click computer>>select manage

then a window comes up and on the left there should be something like local disk or hard drive (something like that). click it and the in the center of the screen you will see the partitons on your drive. select the one you want to shrink and right click and select "shrink". windows wil not allow you to shirnk it to small, so your safe. be sure to defrage first!  

:)

the option to "shrink" doesn't come up when i right click it...

---

### Post by AggieTwist on 2007-11-28
Nevermind, I did it all in gParted and its successfully installed...thanks for everyones help...

---

### Post by natehatewindows on 2007-11-29
sorry about that. i have never done it in XP only vista. im sure there was a way but in all honesty the gpartd way was beter im sure (just thought it would be more easy the other way for you). good job on getting it all up and running. do you like it?

---

### Post by AggieTwist on 2007-11-29
i love it, still have minor issues getting everything to work right...like i had to download codecs for my music and stuff...now my volume isn't quite loud enough...stuff like that...but its an awesome OS.

---

