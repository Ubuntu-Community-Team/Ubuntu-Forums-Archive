---
title: "Did I lose my XP for good?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by VulgarDischord on 2008-03-10
I installed ubuntu last night, and was told before hand, that I would have the option to choose between OS.

Is there a definitive way to tell if I've wrecked my XP?

---

### Post by scragar on 2008-03-10
yeah, boot into it.

after booting you should get a black screen that says something about grub, then either a menu or the message to press esc to enter grub(in which case press escape). pick windows from there and your ready to go.

---

### Post by mips on 2008-03-10
During installation did you repartition your drive or did you install it on the entire drive? If you used the entire drive then you lost WinXP.

Under system or administration there is application call Gparted, start it and tell us how many partitions it shows you and the filesystem type.

---

### Post by Jimmey on 2008-03-10
Or even simpler - ```
 sudo fdisk -l | grep NTFS
```

If that says anything, Windows is there.

---

### Post by scragar on 2008-03-10
> **Jimmey said:**
> Or even simpler - ```
 sudo fdisk -l | grep NTFS
```

If that says anything, Windows is there.

you can also install windows onto fat partitions, so that's not definative.

---

### Post by sayakb on 2008-03-10
@OP
Here's the simplest way.. do you see the Windows partition and the Windows folder in it? If yes, you din't remove XP.. ;)
Also, I hope you didn't go for the "Guided" partition option during Ubuntu installation.

---

### Post by bodhi.zazen on 2008-03-10
Post the output of ```
sudo fdisk -l
```

This will list your partitions and we can see what you have.

---

### Post by VulgarDischord on 2008-03-10
> **LinuxIsInnovation said:**
> @OP
Here's the simplest way.. do you see the Windows partition and the Windows folder in it? If yes, you din't remove XP.. ;)
Also, I hope you didn't go for the "Guided" partition option during Ubuntu installation.


You know, i'm pretty sure I did. does that mean its destroyed?

---

### Post by Oldsoldier2003 on 2008-03-10
> **VulgarDischord said:**
> You know, i'm pretty sure I did. does that mean its destroyed?
yep if thats what you did xp is gone

---

### Post by Ripfox on 2008-03-10
yes.

---

### Post by sayakb on 2008-03-10
Yes, Guided partitioning erases and uses your entire disk. You should've selected the "Manual" option so select which drives to format and which mount points to assign. And all data on your HDD is gone with it. You must be having one single partition now.

---

### Post by zabien1970 on 2008-03-10
> **bodhi.zazen said:**
> Post the output of ```
sudo fdisk -l]
```

This will list your partitions and we can see what you have.

Actually this would be the best way to tell, bodhi.zazen just made a typo, its ```
sudo fdisk -l
``` (remove the last bracket)

---

### Post by bodhi.zazen on 2008-03-10
Thanks, yes I fixed the typo :redface:

I would post a listing of your partitions before you assume anything.

---

### Post by VulgarDischord on 2008-03-10
> **Oldsoldier2003 said:**
> yep if thats what you did xp is gone

So if this is the case, would everything I had saved in windows on that drive be gone as well? all my word documents and such?

I'm mainly concerned that I have a bunch of lingering files that aren't going to get used.

As it sits right now, Ubuntu runs kind of slow. Videos and popular websites won't load and operate as quick as they would with XP.

I just want to make sure I'm not tying up memory with old windows crap.

I want Ubuntu to run as efficiently as possible, It wouldn't hurt my feelings at all to have XP lost forever, just going to be difficult to get the wife and kids to understand whats going on.

---

### Post by Duck2006 on 2008-03-10
In the terminal did you run

sudo fdisk -l

That will tell you what partitions you have on your drive/s in your system.
Then you will know if you have wiped windoze.

---

### Post by bodhi.zazen on 2008-03-10
Assuming you overwrote Windows, which is IMO an assumption still, you *may* be able to recover *some* data with test disk or photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by alphaniner on 2008-03-10
There are two 'guided' partitioning options: 'resize' and 'use entire disk'

[IMG]http://i145.photobucket.com/albums/r208/AshFooYoung/Screenshot.png[/IMG]

Resize is chosen as default, so if you didn't change anything, that is what the installer should have done (I think maybe it depends on the amount of free space on the partition though).  I always use manual partitioning so I don't know how well resizing works, but your windows partition may well still exist.  Then again, if that were the case grub should have presented you with the option to boot to it.  Try the command recommended earlier (Click on Applications at the top right of the screen, then Accessories, then terminal, then type the command at the prompt) to see what your partitions look like.  Regardless of whether or not you toasted windows, your partitioning should not effect performance.  Your swap partition is a consideration, but the installer usually makes that plenty big.  In any case, run the fdisk command! :)

```
[SIZE="5"]sudo fdisk -l[/SIZE]
```

[IMG]http://i145.photobucket.com/albums/r208/AshFooYoung/Screenshot-2.png[/IMG]

---

### Post by VulgarDischord on 2008-03-10
> **alphaniner said:**
> There are two 'guided' partitioning options: 'resize' and 'use entire disk'

<clip>

Resize is chosen as default, so if you didn't change anything, that is what the installer should have done (I think maybe it depends on the amount of free space on the partition though).  I always use manual partitioning so I don't know how well resizing works, but your windows partition may well still exist.  Then again, if that were the case grub should have presented you with the option to boot to it.  Try the command recommended earlier (Click on Applications at the top right of the screen, then Accessories, then terminal, then type the command at the prompt) to see what your partitions look like.  Regardless of whether or not you toasted windows, your partitioning should not effect performance.  Your swap partition is a consideration, but the installer usually makes that plenty big.  In any case, run the fdisk command! :)

```
[SIZE="5"]sudo fdisk -l[/SIZE]
```

<clip>


The most irritating part of all of this, is I'm asking for help and I'm no where near the computer. I did this last night, and it actually kept me awake wondering if I screwed anything up in the process. I thank all of you for your replies. As soon as I get home, I will try all suggested and post and update as to what has happened.

Edit: bodhi.zazen ~ Large images clipped from quote.

---

### Post by SunnyRabbiera on 2008-03-10
good luck.

hopefully you didnt frag your windows stuff up, I know how frustrating that can be.

---

### Post by Duck2006 on 2008-03-10
> Edit: bodhi.zazen ~ Large images clipped from quote.

They sure were big.

---

### Post by alphaniner on 2008-03-10
> **Duck2006 said:**
> They sure were big.

Sorry about that, they were just straight screencaps. :(

> **VulgarDischord said:**
> ...it actually kept me awake wondering...


I'm sure most of us have been there, I know I have.  It sucks having to leave your PC before you can figure out what's happened.  A good piece of advice that I have only recently begun to follow is to record as much as possible of what you do so you can go back and look over it later.  Write it down if you have to, or copy'n'paste and take screencaps when you can.  It can make things much less frustrating, and much more educating!

a9

---

### Post by VulgarDischord on 2008-03-10
> **bodhi.zazen said:**
> Thanks, yes I fixed the typo :redface:

I would post a listing of your partitions before you assume anything.



This is what I'm looking at, what now from here?

andy@Destructor:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0f02c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7062    56725483+  83  Linux
/dev/sda2            7063        7297     1887637+   5  Extended
/dev/sda5            7063        7297     1887606   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec076993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4111    33013575    f  W95 Ext'd (LBA)
/dev/sdb5               2        4111    33013543+   7  HPFS/NTFS
andy@Destructor:~$

---

### Post by bodhi.zazen on 2008-03-10
I am seeing two hard drives.

The first (sda, 60 Gb) has nothing but Ubuntu.

The second (sdb, 41 Gb) has a NTFS partition.

So , lets see what is on the second partition :

In a terminal,

```
sudo mkdir /media/NTFS
sudo mount -t ntfs /dev/sdb5 /media/NTFS
```

And then :

```
gksu nautilus /media/NTFS
```

If that looks like your Windows install, all we need to do is configure grub (to boot windows). If not :(

---

### Post by gecko113 on 2008-03-10
Well if that is the case and XP is gone don't worry u can either re-install it on a partion or u can all linux have full control of you computer and run a virtual machine. I had a similar problem but with vista. Vista commited sucide and has never been back on my laptop. I use the virtual machine to run xp on it. its like a boot camp you can run it while linux is still running. Here is the link that will show you how to install it as well as download the proper packages. [http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php)

---

### Post by roninbk on 2008-03-10
I used Guided and it didn't destroy my NTFS partition.

Then again, I used Vista to repartition my disk, so I had a third Guided option when I installed Ubuntu.(Gutsy) (largest unallocated free space)

So don't say that "if you used Guided, you're screwed."

---

### Post by VulgarDischord on 2008-03-10
> **bodhi.zazen said:**
> I am seeing two hard drives.

The first (sda, 60 Gb) has nothing but Ubuntu.

The second (sdb, 41 Gb) has a NTFS partition.

So , lets see what is on the second partition :

In a terminal,

```
sudo mkdir /media/NTFS
sudo mount -t ntfs /dev/sdb5 /media/NTFS
```

And then :

```
gksu nautilus /media/NTFS
```

If that looks like your Windows install, all we need to do is configure grub (to boot windows). If not :(

That brought me to the contents of my Slave drive. I didn't see anything to do with XP on there. 

It was said that the first hard drive is just Ubuntu, then I fear I've lost XP.

If this is the case, the only thing on my harddrive is Ubuntu and its programs?

---

### Post by Duck2006 on 2008-03-10
> **VulgarDischord said:**
> That brought me to the contents of my Slave drive. I didn't see anything to do with XP on there. 

It was said that the first hard drive is just Ubuntu, then I fear I've lost XP.

If this is the case, the only thing on my harddrive is Ubuntu and its programs?

I would say so then.

---

### Post by bodhi.zazen on 2008-03-10
Well, I am sorry you lost your XP install, but at least we have confirmed that :(

You might be able to recover some files with photorec, or a professional data recovery service.

[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

If you are wanting to try to recover files, STOP running from hard drive (you may over-write files) and attempt recovery from a live CD.

=============

Otherwise it is partition the master drive, re-install Windows, re-install Ubuntu (it is probably easier to just re-install rather then partition and edit your config files).

Be sure to understand Linux partitioning :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by roninbk on 2008-03-10
If you can't save the old system, and you still want to dual-boot Windows, it would be easier to start at the beginning, with a fresh install of both OS's. Make sure you leave an unformatted partition when you install Windows, (or just set aside your slave drive if you want to.) When you install Ubuntu afterward, make sure you point to the largest unallocated free space option.

---

### Post by VulgarDischord on 2008-03-10
Looks I'm a full time Ubuntu user. It's for the best anyway.

---

### Post by Ripfox on 2008-03-10
Hope it is a good experience, I know I haven't had Windows on any of my computers for over a year or so now...and i am happy as can be!

---

### Post by VulgarDischord on 2008-03-10
> **VulgarDischord said:**
> Looks I'm a full time Ubuntu user. It's for the best anyway.

unfortunately, my computer keeps shutting off and turning on by itself.... or did until it just stopped showing a display.

dammit.

---

### Post by Ripfox on 2008-03-11
You should retry a fresh download and install of Ubuntu...it does seem you overwrote your XP install anyways, so why not start over with a fresh disk and install, then come here on how to install all the multimedia stuff and goodies.

---

### Post by VulgarDischord on 2008-03-11
> **ripfox said:**
> You should retry a fresh download and install of Ubuntu...it does seem you overwrote your XP install anyways, so why not start over with a fresh disk and install, then come here on how to install all the multimedia stuff and goodies.

im thinking theres some hardware failure now. My computer will shut off and turn back on by its self. and the duration between switches is getting shorter.

might be time for a new computer.

---

### Post by mips on 2008-03-11
> **VulgarDischord said:**
> im thinking theres some hardware failure now. My computer will shut off and turn back on by its self. and the duration between switches is getting shorter.

might be time for a new computer.

I've seen this on a laptop before. Was a problem with the kernel and the fans would not turn on thus it overheated.

---

### Post by VulgarDischord on 2008-03-11
> **mips said:**
> I've seen this on a laptop before. Was a problem with the kernel and the fans would not turn on thus it overheated.

Well, I let it sit overnight without anypower to it, started it up when i got home about 24 hours later, loaded up ubuntu... checked my system, it shut off..... turned it back on..... checked the cmos and bios... everythings the way it should be... started doing my 198 updtaes. and so far everythings still flying..... heres to hopin, i really want to use this OS... i'm extra excited about it after all this research... Everyone on this msg board has been great.

try to get help like this for windows....

Viva Ubuntu!

---

### Post by VulgarDischord on 2008-03-13
> **VulgarDischord said:**
> Well, I let it sit overnight without anypower to it, started it up when i got home about 24 hours later, loaded up ubuntu... checked my system, it shut off..... turned it back on..... checked the cmos and bios... everythings the way it should be... started doing my 198 updtaes. and so far everythings still flying..... heres to hopin, i really want to use this OS... i'm extra excited about it after all this research... Everyone on this msg board has been great.

try to get help like this for windows....

Viva Ubuntu!

Swapped the PSU, solved the problem.

---

