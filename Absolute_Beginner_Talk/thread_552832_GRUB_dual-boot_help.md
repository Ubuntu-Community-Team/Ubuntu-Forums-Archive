---
title: "GRUB dual-boot help"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by NamedUser on 2007-09-17
Alright here's the deal. GRUB's installed correctly on the MBR, menu opens fine if I want it to, either way I can boot into Ubuntu no problem.
But I have Vista on (hd0, 5) (aka hda5) and no matter what I do it can't load it. Sometimes it tells me that the drive doesn't exist, sometimes it tells me that the partition doesn't exist, but no matter what I've tried it doesn't work.
From what I understand the following is what it should look like:

title Windows Vista
rootnoverify (hd0, 5)
makeactive
chainloader +1

Which doesn't work at all. (Error 12)
To make matters worse, I don't actually have the Vista DVD, just an ISO but no DVD burner or DVDs. (No it's not pirated, I got it through my school's MSDNAA program) I'm heading back to college on wednesday (it starts next monday) and would like to have this problem resolved by then, but if worse comes to worse I'll use linux to save what I can then wipe both and start over with help from friends when I get there.
Anywho... help?

---

### Post by SpiritIsReality on 2007-09-17
howdy

Vista on /dev/hda5
would be (hd0,4) in grub speak
error 12 here
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)
maybe try editing the /boot/grub/menu.lst entry

trails

---

### Post by CaptainInsaneO on 2007-09-17
I agree with fmat.

Remember, count from zero, not one.

---

### Post by NamedUser on 2007-09-17
The following generates an error 12:
rootnoverify (hd0, 4)
makeactive
chainloader +1

The following gives me a "Starting up..." and a very long pause with no activity (assumed lock-up)
rootnoverify (hd0, 4)
chainloader +1


So yeah, still no luck :(
I was able to glean that partition 0 is type 0x83, partition 4 is 0x7 and partition 5 is 0x82, not that I know what format types those match up to (I assume 0x83 is ext#, 0x82 is swap and 0x7 is NTFS?)

PS: I feel stupid for the "count from 0" thing *hits self in face for something that should be obvious to a programmer*

---

### Post by jpyanowski on 2007-09-17
I sure hope that NamedUser checks back here for the answer.:popcorn:

---

### Post by jpyanowski on 2007-09-17
Sorry about the previous post. Was Vista installed first on your box?

---

### Post by NamedUser on 2007-09-17
Order of events:
Win XP installed, ran it for quite a while.
Got Vista, Installed on spare partition with XP (second half of disk), let vista take over dual-booting
Disabled XP access from Vista's dual-boot (sorry XP, but Vista > you in my mind)
Used Ubuntu disk to format XP's space into two spots: space for the OS and swap space.
Installed Ubuntu and let its bootloader (GRUB) take over.
Realized Vista wasn't on the list.
Pain.
Suffering.
Samurai Champloo (I can still access my anime :))

Note: I ran with XP for a few years, Vista since it came out. Ubuntu since... yesterday.

---

### Post by CaptainInsaneO on 2007-09-17
I aplogize, I'm definitely not here to make you feel stupid and that was not my intention. :( It's a common mistake, even for programmers (I forget sometimes myself).

Try adding "savedefault" under your root line.

---

### Post by HimK12 on 2007-09-17
NamedUser...I am having the exact same problem...exact!!!

Now, what I have come to understand is that the problem is that the vista partition is lableled logical (for some ungodly reason)...and it needs to be primary for vista to boot up.

I was looking for how to fix that, and I ran into your thread. Anyways...hopefully we'll both get it fixed soon.

---

### Post by CaptainInsaneO on 2007-09-17
> **HimK12 said:**
> NamedUser...I am having the exact same problem...exact!!!

Now, what I have come to understand is that the problem is that the vista partition is lableled logical (for some ungodly reason)...and it needs to be primary for vista to boot up.

I was looking for how to fix that, and I ran into your thread. Anyways...hopefully we'll both get it fixed soon.

WHAT?! Seriously... every day I find another reason to hate that new Microshaft operating system. Ugh.

You really have something here... windows doesn't like to play with GRUB when it's labelled as logical. As far as I know the only way to fix that is to format... there's more than one way to skin a darn cat though.

Hey. Google, c'mere you. :lolflag:

Edit: I found this: [http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

---

### Post by forestpixie on 2007-09-17
vista really seems to be a bit of a nightmare, I've been looking for this

> title Windows Vista
root (hd0,1)
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
makeactive
chainloader +1

This was the result of a thread I got involved in 3 weeks ago, I assume it worked for that OP as she didn't come back.

Apparently, it confuses vista into believing it's in charge ;) - my words but read that sentiment somewhere here. Obviously the disc refs were from that situation. I don't profess to know if it'll help here. But thought I'd chime in just in case it did :)

---

### Post by NamedUser on 2007-09-17
Unfortunately none of the above stuff worked :(
I think my problem lies in the "makeactive" statement, as whenever I try to use that I get an Error 12, but if I don't it'll lock up on the "Starting up..." part. Could this have something to do with the logical/primary thing?
*le sigh*

---

### Post by slira on 2007-09-17
grub is helping you to get rid of vista...:lolflag:

---

### Post by slira on 2007-09-17
seriously now; try super grub, eventually it will fix your booting problems.
best
slira

---

### Post by NamedUser on 2007-09-17
Yeah... uh... I couldn't get super grub to boot my vista either -_-
It's looking more and more like a wipe is required and I'm not liking it, especially since that'd mean I'd be giving up on linux entirely (and so far I like it.. except that I can't play my games... and it doesn't have visual studio (hey, I got it for free and it's awesome)).

---

### Post by Shazaam on 2007-09-17
BAH. The more I use Linux the less I like Uncle Bill.
Post a copy of fdisk -l here. (small L)
I agree, Vista should be installed first, then resize Vista smaller and then install linux. But with a little creative use of Ubuntu we might get you sorted out.

This is a question for the gurus; couldn't he use gparted and the dd command to clone the partitions so Vista will calm down? Since he has only used ubuntu for a short time maybe delete the ubuntu partition, make a new partition (say hda1), clone the Vista partition (hda5) to hda1 and go from there?

---

### Post by CaptainInsaneO on 2007-09-17
That could work I bet. He'd have to somehow get Vista onto a primary partition though, any ideas on how to do that? I have none. :(

---

### Post by NamedUser on 2007-09-17
"sudo fdisk -l /dev/hda"

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2756    22137538+  83  Linux
/dev/hda2            2757        9729    56010622+   f  W95 Ext'd (LBA)
/dev/hda5            3256        9729    52002373+   7  HPFS/NTFS
/dev/hda6            2758        3255     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order

Question: Why does hda2 overlap exactly hda5 and hda6? And wtf happened to 3 and 4? Not good enough for it? lol

---

### Post by Shazaam on 2007-09-17
AHA!
Type this in a console..
sudo fdisk /dev/hda


This will print out...
example=
# fdisk /dev/hda

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

type m in the console

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): 

type p in a console and post the output here. Don't close the terminal yet.

DO NOT HIT W UNDER ANY CIRCUMSTANCE YET!!!!!!!! (in the terminal)

---

### Post by Shazaam on 2007-09-17
In case we get disconnected here what we want to do is make Vista bootable. You see the * next to hda1 and nothing next to hda5? The boot flag is set to Ubuntu.
If you aren't sure or comfortable about what you are doing while in this part just type in q to exit without saving any changes. If you hit w that writes to the mbr and can render your pc unbootable. ALWAYS wait till you are done to hit w.

---

### Post by NamedUser on 2007-09-17
It prints out more-or-less the same thing, but okay, here ya go...:

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2756    22137538+  83  Linux
/dev/hda2            2757        9729    56010622+   f  W95 Ext'd (LBA)
/dev/hda5            3256        9729    52002373+   7  HPFS/NTFS
/dev/hda6            2758        3255     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by NamedUser on 2007-09-17
Well I toggled the bootable flag on hda5, so do I just wanna tell the thing "w" then reboot?

---

### Post by logos34 on 2007-09-17
I noticed a typo in your menu.lst entry.:
> rootnoverify ([COLOR="Red"]**hd0, 4**[/COLOR])
makeactive
chainloader +1

There shouldn't be a space between the comma and 4.  So try this:

> title Windows Vista
root (**hd0,4**)  -->or 'rootnoverify'
makeactive
chainloader +1

Try it with the boot flag on windows partition.


add:
> 
Question: Why does hda2 overlap exactly hda5 and hda6? And wtf happened to 3 and 4? Not good enough for it? lol

hds2 is an **extended** partition--it CONTAINS hda5 and 6 (logical partitions start numbering with 5)

---

### Post by NamedUser on 2007-09-17
> title           Windows Vista
rootnoverify    (hd0,4)
makeactive
chainloader +1

No go... Whenever the "makeactive" is there I get an error, and without it I get a "Starting Up..." screen that never goes anywhere.

---

### Post by CaptainInsaneO on 2007-09-17
Have you added the boot flag?

Also, did you try putting savedefault under your root line yet?

---

### Post by logos34 on 2007-09-17
> **NamedUser said:**
> Order of events:
Win XP installed, ran it for quite a while.
Got Vista, Installed on spare partition with XP (second half of disk), let vista take over dual-booting
Disabled XP access from Vista's dual-boot (sorry XP, but Vista > you in my mind)
Used Ubuntu disk to format XP's space into two spots: space for the OS and swap space.
Installed Ubuntu and let its bootloader (GRUB) take over.
Realized Vista wasn't on the list.
Pain.
Suffering.
Samurai Champloo (I can still access my anime :))

Note: I ran with XP for a few years, Vista since it came out. Ubuntu since... yesterday.

I just re-read this.  Unless I'm completely mistaken what I think happened is that when you installed vista after XP it detected the former as the 'active' windows partition and placed the boot files there, even though vista takes over as the boot manager, chainloading XP.  When you installed ubuntu root over hda1/XP you overwrote the bootfiles it contained too.  You'll have to find a way to restore those boot files to the vista partition.

---

### Post by NamedUser on 2007-09-17
> **CaptainInsaneO said:**
> Have you added the boot flag?

Also, did you try putting savedefault under your root line yet?
Yeah, that didn't do anything.

> 
I just re-read this. Unless I'm completely mistaken what I think happened is that when you installed vista after XP it detected the former as the 'active' windows partition and placed the boot files there, even though vista takes over as the boot manager, chainloading XP. When you installed ubuntu root over hda1/XP you overwrote the bootfiles it contained too. You'll have to find a way to restore those boot files to the vista partition.

That would explain why it won't let me "makeactive" on the vista partition.. exactly how I would go about restoring it is the real question, in that case.

---

### Post by logos34 on 2007-09-17
I think the only way is through the repair environment on the vista dvd.  Maybe somene else has some suggestions. But if that's the case, you'll need to find a way to burn that iso to a dvd or borrow a copy from a friend.

---

### Post by NamedUser on 2007-09-17
> **logos34 said:**
> I think the only way is through the repair environment on the vista dvd.  Maybe somene else has some suggestions. But if that's the case, you'll need to find a way to burn that iso to a dvd or borrow a copy from a friend.

That's what I was thinking... Well when I get back to school I'll have someone with a DVD drive burn the ISO for me then see if it'll do a "recover" thing without borking ubuntu as well. Thanks for the help guys, I'll post back here when I get a hold of that DVD.

---

### Post by Shazaam on 2007-09-17
Sorry for the delay getting back here.
Yes, what I wanted to do is have you change the bootable flag to Vista but that doesn't seem to have worked. Did you un-flag Ubuntu while you were there? With Vista flagged as boot instead of Ubuntu that might have helped.
With Vista at hda5 I think you will have nothing but trouble trying to fix the problem. You need Vista and all of it stuff loaded on the drive by itself first then resize Vista to add space for Ubuntu. Thats why I was asking about cloning Vista to a new partition.

---

### Post by HimK12 on 2007-09-17
Remember me...I'm the guy with the same problem as NamedUser.

Anyways, dont bother trying to repair vista from vista boot cd, I've done that ..and it does not work.

ALso, I used Gparted to flag vista partition as boot, and unflag the ubuntu one..and vista still does not load.

Oh..and btw...if u uninstall linux now... u still wont be able to get into vista. Your computer will just show no operating system.

---

### Post by NamedUser on 2007-09-17
That's... really crappy to say the least. Worse comes to worse I still have the "wipe both and start over" option available (once I get back to college, that is). Damn good thing I have most of my important stuff on my data drives.

---

### Post by meierfra on 2007-09-18
> Unless I'm completely mistaken what I think happened is that when you installed vista after XP it detected the former as the 'active' windows partition and placed the boot files there, even though vista takes over as the boot manager, chainloading XP. When you installed ubuntu root over hda1/XP you overwrote the bootfiles it contained too. You'll have to find a way to restore those boot files to the vista partition.

But  ubuntu does not use the boot sector of its partition. (Unless you install grub to a partition rather than the mbr)  So maybe the vista boot files did not get erased and still are located in the boot sector of (hd0,0)  (I  have to admit that I don't really  believe this,  but I don' t see any harm trying)  So why  don't you try

title Windows Vista
rootnoverify (hd0,[COLOR="Red"]0[/COLOR])
makeactive
chainloader +1


The real reason why I don't think this will work, is  that I have not seen anybody who was able to boot windows xp or vista on an extended partition.  But I'm not all that experienced so please correct me if I'm wrong about this.

On the other hand  I don't  see any compelling reason to reinstall ubuntu. Reinstalling vista on a new primary partition should be sufficient.

---

### Post by logos34 on 2007-09-18
> **meierfra said:**
> I have not seen anybody who was able to boot windows xp or vista on an extended partition.

you can as long as there is a (prexisting) windows 'master' primary partition (i.e. hda1) to host the boot files.  (more on windows mutibooting [ here]("http://www.goodells.net/multiboot/index.htm")).  That's how I had mine set up until recently--main windows partition (xp pro) on first partition (primary), and another (xp home) inside an extended on hda6.

---

### Post by meierfra on 2007-09-18
>  (more on windows multibooting  here). 

Thanks for the link. I read it and now understand more or less what is going on. But not enough to offer any alternative to reinstalling vista on a primary partition.

---

### Post by HimK12 on 2007-09-18
HALLELUJAH....I got it to work.

Read how:

1) Download hiren's boot manager disk, burn it to cd, and then boot ur computerfrom it.

2) Go to hiren's disk partition menu, select any one of the disk partition app (i used acronis). There you'll see your 3(or more) partitions..and u'll see win vista ntfs partition marked as logical.

3) Right click on it, and convert it to primary. Flag it...and ur partition will be converted to primary. Then exit.

4) Now, YOU NEED A VISTA BOOT CD. If you dont have that, then u can't boot into any of ur OS at this point. Anyways, there is an option called repair startup (or something similar). Select that and reboot.

5) Now, boot with hiren again. Go to disk partition manager, and format linux and linuxswap partition.

6) reboot.

7) At this point your computer is dead... Grub loads and shows you error.

8 ) don't worry...run ubuntu cd, and reinstall it. Now that we've marked windows partition primary, repaired its startup and cleaned off old ubuntu settings, this reinstall will fix it.
After you reinstall it, you'll see a vista/longhorn loader in ur grub menu.

Hope that helps...lemme know if there are any questions.

Below is my menu.lst

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9703a1aa-1dbd-45cb-a5c1-c7f763523f39 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9703a1aa-1dbd-45cb-a5c1-c7f763523f39 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by NamedUser on 2007-09-18
Sweet! I'll try this out tomorrow night when I get my **** back together at college, 'cause that's where the Vista disk is.

---

### Post by NamedUser on 2007-09-18
Hmm... any particular reason I couldn't just leave Ubuntu on there and change GRUB myself? As long as it gets marked primary and repaired I should be good, right?

---

### Post by meierfra on 2007-09-18
> Grub loads and shows you error.
 don't worry...run ubuntu cd, and reinstall it. 

This confused me too. But I think HimK12 wants you to reinstall "grub" and not "ubuntu".

---

### Post by CaptainInsaneO on 2007-09-18
> **NamedUser said:**
> Hmm... any particular reason I couldn't just leave Ubuntu on there and change GRUB myself? As long as it gets marked primary and repaired I should be good, right?

I agree with meierfra, I think he meant "reinstall grub". There's no particular reason at all that you couldn't leave Ubuntu on there. :)

---

### Post by HimK12 on 2007-09-19
If you know how to change grub then by all means give it a shot. I didn't ..so I just copied my files to usb and reinstalled ubuntu.

and while I know some smart ppl will be reading this message...can anyone tell me if I can get digital rendering to work on my ati integrated x200 card or should I go to lower version of ubuntu. Sorry for posting my question like this..but it seems no one heeds to the ati problems anymore in main board.

---

### Post by NamedUser on 2007-09-20
So... I boot up the vista DVD after setting the NTFS partition to primary, and lo' and behold it doesn't see a windows partition to be repaired, and thus failed. So.. anyone have another clue?

---

### Post by HimK12 on 2007-09-20
wow..that shouldn't happen. Did you remember to flag the partition as well?

---

### Post by NamedUser on 2007-09-20
you mean as bootable or what?

---

