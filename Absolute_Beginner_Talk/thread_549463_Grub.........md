---
title: "Grub........"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by richardgundersen on 2007-09-12
Hi

Thought all was going well until I realised Grub had stopped XP and Vista from working. Please please could someone suggest the correct entries for Vista and XP based on the settings I have posted below? I would be eternally grateful! 

Also in addition to changing the Grub settings, if there is something else I need to do afterwards like fix the Vista/XP MBRs, then please tell me. I'm really not sure what I should be doing.

I have Vista installed on sda1
I have Ubuntu root (/) on sda2
I have XP installed on sdb1

My BIOS treats sda as the first hard disk. sda is a SATA disk while sdb is IDE.

Only Ubuntu boots at present. Vista was working right up until I installed Ubuntu. I can see all my XP & Vista files but I've no idea if XP is bootable any more. 

I've been messing with grub (press 'e' at bootup to edit the grub entries but no success so far. I've been trying something like

title Vista
root (sda1, 0)
savedefault
makeactive
map (sda1) (sda2)
map (sda2) (sda1)
chainloader +1

Nothing I try works. I get various errors like 'Error 23 can't parse number'

Please help - thanks!

---

### Post by benerivo on 2007-09-12
Have you tried...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Vista
root		(sd0,0)
savedefault
makeactive
chainloader	+1

# on /dev/sdb1
title		XP
root		(sd1,0)
savedefault
makeactive
chainloader	+1
```

You could also try the map function that you have in your example, if the above doesn't work. Or possibly even using 'h' instead of 's'.

---

### Post by richardgundersen on 2007-09-12
Hi benerivo

Thanks for the suggestion. I haven't tried what you suggested before because I thought I always had to have a map function in there. 

I will certainly try out your suggestion in the next few minutes though. I'm currently writing "Super Grub Disk" to a blank CD because I also read somewhere that it might also help me. 

Once my DVD writer has finished I will try out your tips though - thanks!

---

### Post by richardgundersen on 2007-09-12
Hmm, doesnt seem to work. I still get 'Error 23 can't parse number'. I tried a few variations that I thought might be sensible too with no luck. 

For some reason Super Grub Disk doesn't like my DVDs either. I think the gods are conspiring against me tonight....

---

### Post by Polemistis on 2007-09-12
> **richardgundersen said:**
> Hi

Thought all was going well until I realised Grub had stopped XP and Vista from working. Please please could someone suggest the correct entries for Vista and XP based on the settings I have posted below? I would be eternally grateful! 

Also in addition to changing the Grub settings, if there is something else I need to do afterwards like fix the Vista/XP MBRs, then please tell me. I'm really not sure what I should be doing.

I have Vista installed on sda1
I have Ubuntu root (/) on sda2
I have XP installed on sdb1

My BIOS treats sda as the first hard disk. sda is a SATA disk while sdb is IDE.

Only Ubuntu boots at present. Vista was working right up until I installed Ubuntu. I can see all my XP & Vista files but I've no idea if XP is bootable any more. 

I've been messing with grub (press 'e' at bootup to edit the grub entries but no success so far. I've been trying something like

title Vista
root (sda1, 0)
savedefault
makeactive
map (sda1) (sda2)
map (sda2) (sda1)
chainloader +1

Nothing I try works. I get various errors like 'Error 23 can't parse number'

Please help - thanks!

assuming ur linux OS works and windows one does, i would do the following:

Insert your windows CD
let it boot and enter the recovery console
In recovery console type
```
fixmbr
```

This will make windows boot menu load without linux (at this moment)

Now, log into windows. and install grub on windows... download the software
in the menu.lst file in grub folder c:\grub, copy the one from ur linux partition here(u can use a program called ext2dos i think.... i can find out if u want).
Install the grub (the readme file shows how) but its something like
grubinstall menu.lst
possibly with stage1 or something... post here i can find the exact command.

Modify ur boot.ini file (c:\boot.ini), adding the line 
```
Grub="c:\grub"
```
now when u restart, the windows boot loader will show. Select grub and the grub menu will load.
If u wanna load vista or xp... select anything but GRUB.

NOte: your intiial boot loader will be windows, and linux bootloader wqill load when u select grub.
I prefer the Windows bootloader over grub. Anwyays... this should fix your window loading problem.

If u really want... u can make it go straight to ubuntu sintead of grub menu... but not advised in case u hav more than one linux on ur system.

Any more stuff,, jst ask

---

### Post by richardgundersen on 2007-09-13
Thanks for your tips Polemistis. It got a bit late yesterday but I'll try out your suggestions when I get home tonight. 

I totally trashed it by using the Vista disk to try and recover something. Now I have three operating systems on my PC and none of them boot at all!

I was just wondering, is there something particularly bad about the way my disks are arranged? I only have two disks, and three partitions. Surely this isn't such an unusual situation. The only thing I can think of is that in my BIOS, the SATA disk is first, and the IDE disk is second. 

Is there some rule of thumb that says it's better for Grub if the IDE disk is first in the BIOS? (The IDE disk is a master to a slave IDE DVD writer too if that's relevant....?)

---

### Post by richardgundersen on 2007-09-13
Anyone please? Really appreciate any feedback

---

### Post by Bothered on 2007-09-13
Could you type the following in a console (in ubuntu):

```
cat /boot/grub/menu.lst
```

and post the results here.

---

### Post by Bothered on 2007-09-13
Are you still booting from your ubuntu partition? I wouldn't install grub on your windows partition just yet.

---

### Post by confused57 on 2007-09-13
These entries "may" boot your Windows:
```
title   Vista
rootnoverify  (hd0,0)
makeactive
chainloader +1
```

and

```
title   Windows XP
rootnoverify  (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

You would need the map lines to boot XP...also, grub designates drives as hdx, regardless of whether they're sata or pata.

---

### Post by richardgundersen on 2007-09-13
Hi thanks for the recent replies both of you. 

I'm heading off for home now so I will get my menu.lst contents and also try those config params when I get back. I didn't realise that grub ONLY used hd0/hd1 rather than sda etc for SATA so that's well worth trying. 

First I need to boot into *some* kind of operating system - the whole thing is messed up at the moment. I'm pinning my hopes on Super Grub Disk so maybe that will get my bootloader back. :)

I'll post an update when I can - thanks again

---

### Post by richardgundersen on 2007-09-14
Thanks for everyone's help on this. Here's where I am and what I did in case it's any help:

Ubuntu + Vista both boot!
XP doesn't boot (starting to wonder if I actually care about XP to be honest)

I booted the Vista DVD and skipped straight to the 'Repair PC' and 'Command Prompt' bit (vista didn't even detect any instances of Vista on my PC hmmmm....)

From command prompt, run: bootrec /FixBoot
This sorts out the MS bootloader in the partition where you installed Vista (in case you have 'missing NTLDR' (XP has overwritten the vista BL) or 'missing BOOTMGR' messages). 
Now that the Windows partition has the boot files needed to boot, you need the config (BCD or something) so run bootrec /RebuildBDC. It will kind of make the windows version of menu.lst.

Right, so my Windows partition is all good. Now I need the main bootloader (of the whole system) i.e. grub to be installed since the last couple of commands have a side effect of screwing the main boot thingy up. This is easy though - just install grub again using the ubuntu disk or 'Super Grub Disk' which was quite easy to use and very Super as the docs say he :) 

Now Grub is the first bootloader that is encountered. It gives me the option of loading Ubuntu or if I choose Vista, it invokes the vista bootloader (discussed above). 

The only bit left is to make sure grub knows where vista is, so I entered the following in menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I hope this helps someone

---

### Post by Polemistis on 2007-09-15
> **richardgundersen said:**
> Thanks for your tips Polemistis. It got a bit late yesterday but I'll try out your suggestions when I get home tonight. 

I totally trashed it by using the Vista disk to try and recover something. Now I have three operating systems on my PC and none of them boot at all!

I was just wondering, is there something particularly bad about the way my disks are arranged? I only have two disks, and three partitions. Surely this isn't such an unusual situation. The only thing I can think of is that in my BIOS, the SATA disk is first, and the IDE disk is second. 

Is there some rule of thumb that says it's better for Grub if the IDE disk is first in the BIOS? (The IDE disk is a master to a slave IDE DVD writer too if that's relevant....?)

whoops... sorry if it trashed it...
but it should have worked... u should do fixmbr (if bootloader was installed in master boot sector, which i presumed it was), or fixboot (if first partition on HDD).

But seeing that you got it working now with fixboot thats good :D

---

