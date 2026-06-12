---
title: "Removing Grub loader and Ubuntu"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by frankiethepill on 2006-04-29
Sacrilege I know but Grub is giving me problems running a dual boot system so I'm going to rejig things and start Ubuntu again- how do I remove the grub loader and put the disk back to its original state?

---

### Post by Rinzwind on 2006-04-29
You do not need to.

Reinstalling also deletes Grub cuz the settings for Grub are inside a file on your disc.
Just redo your install and you are good to go.

But isn't it possible to fix your problem? Fixing would help you get an insight into Grub and it'll make you proud you won  :KS

---

### Post by frankiethepill on 2006-04-29
I really want to put Ubuntu onto another machine and put the partitioned disk back to as it was before Ubuntu- I could just remove the partition but the disk is set up with NTFS and Win XP doesn't come with FDISK any more which would have put things back with the /MBR option to restore the boot sector. I might be able to fing an old version of FDISK but am not sure it will be ok with the NTFS disk- I can't afford to get it wrong.

---

### Post by Rinzwind on 2006-04-29
Ahhh

boot Windows with your CD.
choose repair and at the C: typ

FIXMBR

That kills any bootloader you installed.

[msdn](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

And after a reboot you can then reformat the Linux partition back to Windows format.

---

### Post by Herman on 2006-04-29
You could either install GAG boot manager, or restore your old Windows XP boot sector with a Windows 98 boot disk from bootdisk.com. More details [here.]("http://www.users.bigpond.net.au/hermanzone/p18.htm")  I hope I'm being helpful, regards, Herman. :D

Edit, Rinzwind's method is the best if you can do it that way, but I thought you meant you couldnt do it that way. Some Windows XP CDs (suah as 'System Recovery' disks can't.

---

### Post by frankiethepill on 2006-04-29
Sorted- thanks for all your help. Used the Win install disk and did the FIXMBR option. Never seen that before but worked like a charm.

---

