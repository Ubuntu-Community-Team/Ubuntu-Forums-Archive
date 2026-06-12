---
title: "Need help with dual boot...Thanks"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-18
I attempted to install Ubuntu 5.10 as a dual boot with Windows XP.  I followed advice from this article:  [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/) and placed GRUB in the Linux partition, which I made bootable, and referenced it in the Windows boot.ini file.  When I boot up, it opens the boot loader, but when I select Ubuntu Linux, nothing happens--just a blank screen.

I'm thinking of just repartitioning the drive and starting over (hopefully, preserving the Windows partition), and my question is:  is it safe to place GRUB in the master boot record (MBR) as Ubuntu wants to do?  The article recommends against it.  Will I run a risk of losing the ability to boot into Windows?

Also, just in case there's a way to fix the problem without starting over, here's the boot.ini file:

[boot loader]

timeout=20

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\UBUNTU.bin="Ubuntu Linux"


UBUNTU.bin is a separate file that I created and mounted according to the instructions in the article.  I followed everything literally except that I substituted my partitions.

Any advice or ideas?  I'd be grateful.  Thanks.

---

### Post by Remmelas on 2005-11-18
I let Ubuntu place grub on the MBR, and have always done so with my Linux installs... Grub is so much easier to use than the windows boot loader.  You won't likely experience any troubles at all if you let Ubuntu/Grub do their thing.

---

### Post by aysiu on 2005-11-18
No offensive, but that article (and ones like it) are pieces of s. I got sucked into one of those the first time I installed Linux and thought, "What a pain in the a!" It's because of articles like that that I thought Linux was too difficult. It's not. Articles like that *make* it difficult for no good reason. 

Installing Grub to the MBR is the way to go, definitely. Bottom line:

1. Windows' boot loader will never recognize Ubuntu unless you do all sorts of electronic backflips to make it recognize Ubuntu.
2. Ubuntu's boot loader will almost always recognize Windows right away and automatically add Windows to the boot menu.

So why would you want to make Windows' boot loader in charge of a dual boot? I hate articles like that.

For a better tutorial on dual-booting, check [this](http://users.bigpond.net.au/hermanzone/) out.

---

### Post by earobinson on 2005-11-18
[QUOTE=aysiu]Windows' boot loader will never recognize Ubuntu unless you do all sorts of electronic backflips to make it recognize Ubuntu.[/QUOTE]

rofl best quote ever

---

### Post by deNoobius on 2005-11-18
OK, thanks everyone!  Thanks for the "good" article, and for the reassurance about the MBR.  I'll let you know how it goes when I redo things--perhaps tonight.

---

### Post by BLTicklemonster on 2005-11-19
I tried looking at both, and neither made any sense to me.

I'd like to know what I can do, now that I have installed unbuntu and have a separate disk with windows on it that was not hooked up at installation, to have the same boot screen that I see on a different computer that I installed ubuntu on which had a windows hd in slave.

Can it be done, if so, how?

Not, "please send me to a site that makes no sense", but rather, "please tell me".

Thank you.

*edit:

[http://www.ubuntuforums.org/showthread.php?t=92161](http://www.ubuntuforums.org/showthread.php?t=92161)

Ookay, got that far, I still need to know if there's something I can edit in ubuntu so that I can dual boot, though.

---

### Post by aysiu on 2005-11-19
If the hermanzone dual-boot guide makes no sense to you, I highly doubt anyone's written explanation in a forum post will be any clearer.

Herman's taken a lot of time to outline the entire dual-boot setup process step by step (with screenshots and explanations).

---

### Post by deNoobius on 2005-11-19
I (OP) should mention here that I got my dual-boot situation straightened out.  The solution involved editing a line in the Grub boot menu, in this thread:

[http://www.ubuntuforums.org/showthread.php?t=92333](http://www.ubuntuforums.org/showthread.php?t=92333)

---

### Post by BLTicklemonster on 2005-11-19
[QUOTE=aysiu]If the hermanzone dual-boot guide makes no sense to you, I highly doubt anyone's written explanation in a forum post will be any clearer.

Herman's taken a lot of time to outline the entire dual-boot setup process step by step (with screenshots and explanations).[/QUOTE]

All I see is stuff on how to do it from install. I already have ubuntu installed, and have a hd with windows on it. I now have it slaved, and can access it well enough, but I want to have the option to boot from it as well.

I will go back and click on every thing again and try again.


*edit:

Nope, all I see is stuff on how to do it from install.


and let me put it another way: oh it makes perfect sense from the installation side of it all. Shoot, I installed ubuntu on my son's computer with the windows hd slaved, and it picked it up automatically, no prob, so that how to doesn't apply to me. What doesn't make sense is that there's nothing on how to do it after installation when you decide, "oh gee, maybe I should have done it that way" but you don't want to reinstall everything.

---

### Post by BLTicklemonster on 2005-11-19
```
bill@ubuntu:~$ sudo fdisk -l
Password: berfunkleykabiblermonickerstifirneglorpagordonkgordonkpfftsssssaaaaah

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161   83  Linux
/dev/hda2            9730       10011     2265165    5  Extended
/dev/hda5            9730       10011     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
bill@ubuntu:~$

```

so my xp is on hdb1, what do I put? I put 1,0 not knowing any better, thinking that slave would be 1, and first partition would be 0. Good news is, it now shows up when I hit esc (wish I didn'thave to do that, but would have an automatic choice, but if it will work, I'll deal with it).

---

### Post by jeffjanzen on 2005-11-20
[QUOTE=BLTicklemonster]so my xp is on hdb1, what do I put? I put 1,0 not knowing any better, thinking that slave would be 1, and first partition would be 0. Good news is, it now shows up when I hit esc (wish I didn'thave to do that, but would have an automatic choice, but if it will work, I'll deal with it).[/QUOTE]
if the file /boot/grub/menu.lst includes this (near the bottom, probably):
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```
you should be in business.  are you saying this is included in menu.lst and you're still having problems?  you're saying you want to automatically be given a choice between operating systems?  that's what grub is made for.  you have to tell it how long to wait for you, though.  that's also in menu.lst under the label "timeout".
p.s. i think it's kind of confusing that fdisk calls your windows partition "hdb1" and grub wants you to say "hd1,0".  i think there should be some kind of standard....

---

### Post by BLTicklemonster on 2005-11-20
[QUOTE=jeffjanzen]if the file /boot/grub/menu.lst includes this (near the bottom, probably):
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```
you should be in business.  are you saying this is included in menu.lst and you're still having problems?  you're saying you want to automatically be given a choice between operating systems?  that's what grub is made for.  you have to tell it how long to wait for you, though.  that's also in menu.lst under the label "timeout".
p.s. i think it's kind of confusing that fdisk calls your windows partition "hdb1" and grub wants you to say "hd1,0".  i think there should be some kind of standard....[/QUOTE]
Yes, that's exactly what I edited it to say. But I have to press esc to bring up the option to boot to a different os, ... whoa, wait a minute...

....no wait... backing up a bit, it actually says this:

```
# This entry automatically added by the Debian installer [COLOR="Red"][B]for a non-linux OS
# on /dev/hda1[/B][/COLOR]
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1
```


Problem is, XP is not on /dev/hda1. So I'd imagine that this line

```
root    (hd1,0)
```

is actually wrong. I wonder if editing out root, and making it say this

```
title        Microsoft Windows XP Professional
hd1,0
savedefault
makeactive
chainloader    +1
```

instead would make it work, seeing as how it's on hd1,0 not root or hda1?

If you don't see me for a few weeks, then in lieu of flower, send money to the American Fund for People Who Ought To Know Better, But Tweak Stuff Anyway.



*edit:

Nope, didn't work. 
shoot, I have a machine that had ubuntu installed on it with xp slaved already, but the drive is out because we ran into this same kind of problem with it. Windows wouldn't load if chosen, either. I'd like to compare those lines. I guess once the kid is done playing, I'll hook it up and compare. Problem is, like I said, it won't boot to windows, either.

Gotta be a way to do this.

---

### Post by aysiu on 2005-11-20
[QUOTE=BLTicklemonster]Yes, that's exactly what I edited it to say. But I have to press esc to bring up the option to boot to a different os, ... whoa, wait a minute...

....no wait... backing up a bit, it actually says this:
[/quote]
```
# This entry automatically added by the Debian installer [COLOR="Red"][B]for a non-linux OS
# on /dev/hda1[/B][/COLOR]
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1
``` It shouldn't make a difference. Lines with the # sign in front of them are just comments to describe what's actually in the configuration file.

> 
Problem is, XP is not on /dev/hda1. So I'd imagine that this line

```
root    (hd1,0)
``` 
is actually wrong. Yes, it would be.

> I wonder if editing out root, and making it say this

```
title        Microsoft Windows XP Professional
hd1,0
savedefault
makeactive
chainloader    +1
```

instead would make it work, seeing as how it's on hd1,0 not root or hda1? No. *root* describes where it is. (hd1,0) is the location. hd1,0 = hda1 (the 1 is an a, the 0 is a 1).

Can you type this in a terminal? ```
sudo fdisk -l
```

---

### Post by BLTicklemonster on 2005-11-20
That's how I knew it was hdb1

```
bill@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161   83  Linux
/dev/hda2            9730       10011     2265165    5  Extended
/dev/hda5            9730       10011     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
bill@ubuntu:~$


```

>  No. root describes where it is. (hd1,0) is the location. hd1,0 = hda1 (the 1 is an a, the 0 is a 1).
Therefore, hard drive hdb1 would be hard drive 2, so that ought to be

```
root        (hd2,0)
``` ?

---

### Post by aysiu on 2005-11-20
Okay. If it's hdb1, then what you want is not ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1
``` You want this instead ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by steve.horsley on 2005-11-20
this is wrong:
```

title        Microsoft Windows XP Professional
hd1,0
savedefault
makeactive

```

You must say root and have brackets round the drive name:
```

title        Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader    +1

```
I hope this one works for you
Steve

---

### Post by BLTicklemonster on 2005-11-20
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
chainloader    +1
```

tells me that there is no such drive

and the way I did it originally, based on thinking that hdb1 meant that 1 was the second drive:
```
title        Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader    +1
```

Gets me this:

```
Originally Posted by Souljah
root (hd0,5)
File System Type Unknown, partition type 0x7
savedefault
makeactive

Error 12: Invalid device requested
```


BUT, I'll try this:

```
title        Microsoft Windows XP Professional
(hd1,0) [COLOR="Red"]or possibly even (hd2,0)[/COLOR]
savedefault
makeactive
```

just for yucks.


*edit:

Neither of which works as you both know.

I get this error on both:

```


Error 13: Invalid or unsopported executable format
```

Question, because xp is so bossy, if I wanted to boot from it by changing boot order in bios, I'd set it as the master, and ubuntu as the slave, right? I'd normally then set the second or hdd2 as the one to boot from, but when I would ... (hey, I wonder....) use it to boot from hdd1 when I need windows, which would be soon, because none of my burners see my dvd rom and dvd rw correctly. They both see them backwards. If I am in gnomebaker or k3b, and I press to eject the dbd rw, it ejects the dvd rom, and vice versa, which impedes me backing up the kid's dvds, which I am behind on since I undertook this Ubuntu thing my wife hates so much, lol.

---

### Post by BLTicklemonster on 2005-11-20
Oookay, so if I physically change the drives, putting xp to master, ubuntu to slave, and try to boot from hdd0, it will boot windows, if I set it (bios) to boot from hdd2, I get an unrecoverable error, nothing works, bash something says that I can sudo or anything.

which means I need to edit sudo gedit /boot/grub/menu.lst apparently. 

BUT, due to circumstances, I wonder if it would be 

root     (2,0) /

lmao.

weeeeeeeeeeee!!!



(what's this? Ticklemonster's not going off the deep end and ranting and raving about all kinds baloney? Could it be he has calmed down? ... nah, I'm ranting on the inside, but on the outside, I have become PLEASANTATTITUDEMONSTER!!! for some insane reason.)

---

