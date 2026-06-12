---
title: "Cannot boot Windows XP"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by cledezma on 2006-04-06
Hi:

I am very sorry if this type of question has been posted before, but I tried some of the things recommended and I still cannot make Windows XP "come back to life".

I wanted to try Linux and a friend recommended me Ubuntu. I had Windows XP in my notebook, so I backed-up my files, partitioned my disk using Partition Magic 8.0, and then installed Ubuntu. Ubuntu is working fine (except for the wireless connection), but I cannot make Windows XP boot.

The information I see in System/Administration/Disks/Partitions is:

Partition 1
Device: /dev/hda1
Filesystem: Windows NTFS
Access Path: /media/hda1

Swap Partition
Device: /dev/hda3
Filesystem: Memory Swap

Partition 2
Device: /dev/hda2
Filesystem: Extended 2
Access Path: /

This is what I have at the end of the menu.lst file:

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader	+1

Any ideas of what the problem is? Should I try to use "fixmbr" approach?

Thanks!.

---

### Post by kaffeine on 2006-04-06
more info needed - 

do you get the grub screen on boot? what are the options listed there?

your menu.lst suggests that windows XP should be one of the grub options. what happens (error message) if you choose windows XP?

---

### Post by cledezma on 2006-04-06
Hi Kaffeine:

Thanks for your help.

Yes, I see the grub screen on boot. The options are:

Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest 86+
Windows XP

If I choose XP I first see the typical Windows logo with black background (and the blue horizontal line moving from left to right). After that I see 2 blue screens. The first one goes very fast and I cannot read it. The second one says:

STOP: c000021a {Fatal System Error}
The Session Manager Initialization system process terminated unexpectedly with a status of 0xc000003a (0x00000000 0x00000000).
The systema has been shut down.

After that I have to turn my notebook off manually.

Thanks!

(I will be back in 1 hour and a half)

---

### Post by black hole sun on 2006-04-06
Ouch! 

That looks pretty bad. Sounds like Partition Magic hosed your install (Ubuntu's installer won't touch your windows stuff unless you tell it to).

Check out /media/hda1 while in ubuntu; you should at least able to recover important files from your windows install.

---

### Post by vyruss on 2006-04-06
**Do not use** the fixmbr method or you will **not be able to boot Ubuntu** unless you reinstall grub!

This Windows section works for me. You could try it in your **menu.lst**:```
title           Windows XP 
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Always keep a backup of menu.lst before changing it! ;)

However, it appears that since the windows logo appears, it must be some problem with windows and not the bootloader.

---

### Post by klichev on 2006-04-06
The problem is in your Windows - something has gone wrong with it. (Ooops, it seems that vyruss and I have posted right after another ;-)

---

### Post by vyruss on 2006-04-06
From what I can see in other web forums, the easiest way to repair this would be to do an in-place reinstallation of Windows XP [like this page describes]("http://support.microsoft.com/default.aspx?scid=kb;en-us;Q315341"). 

However, after the reinstallation, you will initially not be able to boot into Ubuntu until you reinstall GRUB, because the bootloader will be overwritten by Windows. Do you know how to reinstall GRUB?

---

### Post by cledezma on 2006-04-06
Thanks a lot for all the replies ...

-black hole sun: fortunately I can see basically everything in /media/hda1
-vyruss(1): that is the menu.lst I had before, and it did not work.
-vyruss(2): I think I am going to try that, but I don't know how to reinstall GRUB. Is it too difficult?

Thanks again

---

### Post by ubuntuuser on 2006-04-06
No, it's actually fairly easy. There are some ways to do this. The way I do it is this:

1) After installing windows, boot from a linux livecd of your choice. Once it has booted, type ```
mount
``` and see if your ubuntu partition is already mounted somewhere. If it is mounted, go to 3),

2) So it's not mounted. Type ```
mkdir ~/ubuntudrive
mount /dev/hda2 ~/ubuntudrive
``` to mount it. Replace hda2 with the correct one.

3) I just assume that the partiion is mounted at ~/ubuntudrive. If it's not, use the correct path instead, Now that your drive is mounted, we are almost there. Type ```
chroot ~/ubuntudrive /bin/bash
```to make your ubuntu partition become the root directory. Then just type ```
grub-install
``` and reboot.

---

### Post by Ric95 on 2006-04-06
I had the same problem. It turned out that Partition magic gave my Windows partition the 'hidden' property.  Try rebooting with any fdisc type program and make sure its not hidden.

---

### Post by vyruss on 2006-04-07
Another way to reinstall GRUB is to boot to your rescue system from the Ubuntu CD, and when it asks you to choose a partition, press **Esc** and you will be taken to the menu. There is an option there for GRUB reinstallation I think. But ubuntuuser's way is the proven way to do it :)

---

### Post by bigken on 2006-04-07
Personally I would do a repair install of windows xp (backup data 1st) then boot from your ubuntu disc when you get to the partion part press escape and got to
install grub then reboot ;)

---

### Post by kaffeine on 2006-04-10
here are two options you can give a shot at and see if one of them works if you are not ready to reinstall grub or windows:

1. boot from the partition magic rescue disks - usually partition errors (such as the one Ric95 mentioned) get fixed when a disk manager software looks at the partition table. if your laptop doesn't have floppy drive, try using gparted from ubuntu to see if it flags up any error. my guess is this probably won't resolve your error, but it's worth a shot.

2. boot into ubuntu, and mount the windows partition. navigate to \windows\system32 and rename the file 'system' to 'system.old' (backup)

now copy the file 'system' or 'system.bak' from \windows\repair to \windows\system32 (rename it to 'system' if its originally system.bak, obviously)

what you are basically doing here is restoring your windows system to a post-setup state. 

let us know if this works for you. good luck!

---

### Post by new2linux2009 on 2006-04-10
](*,) Do NOT use partition magic...I messed up two computer using that pile of crap...:(

---

