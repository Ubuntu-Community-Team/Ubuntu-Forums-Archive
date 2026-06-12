---
title: "HELP Ubuntu killed PC"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ScottY_ on 2007-06-21
right i had problems with my resolutino before so i was reinstalling i went for food came back laptop is off.
Ok didnt do that before. Turn on get this:
```
GRUB Loading Stage1.5.

GRUB loading, please wait...
Error 5
_
```
Now nothing loads no way of loading ubuntu or windows. This sucks wtf do i do. Dell media direct doesnt even load! 
I can access my BIOS and run ubuntu off the cd it allows me tn install but only on the whole drive i need my windows partion!

Please help :( anyway i can remove ubuntu partion and grub through the live cd.
Currently posting from my N95 wich is slow :@

---

### Post by rich.bradshaw on 2007-06-21
Boot from WIndows recovery disk, go to recovery console, type,

fdisk /mbr

restart.

Fixed.

Likely you didn't read something and messed the install up. If the live-cd can't see the Windows partition, you deleted it when installing.

---

### Post by overdrank on 2007-06-21
> **ScottY_ said:**
> right i had problems with my resolutino before so i was reinstalling i went for food came back laptop is off.
Ok didnt do that before. Turn on get this:
```
GRUB Loading Stage1.5.

GRUB loading, please wait...
Error 5
_
```
Now nothing loads no way of loading ubuntu or windows. This sucks wtf do i do. Dell media direct doesnt even load! 
I can access my BIOS and run ubuntu off the cd it allows me tn install but only on the whole drive i need my windows partion!

Please help :( anyway i can remove ubuntu partion and grub through the live cd.
Currently posting from my N95 wich is slow :@

Hi apparently the laptop shut down during install are you sure you cannot use the manual partition in the live cd to install ubuntu and install the grub. This way windows should not be affected.:(

---

### Post by ScottY_ on 2007-06-21
@rich, not sure if i know where the disk is :S

@Overdrank yes i can do manual forgot about that. All it sees is /dev/sda which appears to be the whole drive. Before i had my windows partion of 40GB or so and 12GB of free space for Ubuntu, and some other things for Dell rubbish. Now the Ubuntu section has gone, and no free space visible.

---

### Post by ScottY_ on 2007-06-21
Right i found my Windows Install disk, i shoved that in i hir R to load the recovery console but it asks me for windows something i hit 1 and that seems to have worked but then i get asked for my administrator password, so i tried my password and admin and administrator all 3 were wrong,i can't get far enough to fdisk! Windows is bloody annoying, Can't wait to get a f'ing Mac.

Anybody else got any ideas, please :) I can see my windows files from the Live CD so i kow it is still there.

---

### Post by vexorian on 2007-06-21
Who installed the OS in the first place? During first XP install the admin password is set, so you will have to ask him about this. If you did and forgot your admin password then...

If you have access to the partition from live cd, you CAN restore the windows MBR record using LILO and possibly grub as well, I know this because I once ruined some computer's MBR and I only got Slax live-cd and internet access at the moment to fix it.

I am gonna look for the howto that explained how to restore it, but know that there are ways to get rid of the Windows XP admin password if you forgot, although that's also something I don't remember correctly, it is google time for me it seems

---

### Post by alienexplorers on 2007-06-21
Try inserting your Live CD.  See if the ubuntu partition is there. If not reinstall Ubuntu.  If so go to Terminal and type sudo grub.
Enter > find /boot/grub/stage1
You will get an output such as (hd#,#)
Enter > root (hd#,#)
Enter > setup (hd0)
exit grub editor
reboot system and pray.

---

### Post by ScottY_ on 2007-06-21
Right i'll give that ago, i din't set the password, infact as far as i knew the administrator when booting through safe mode had no password so Dell have gone and played with it :x stupid Dell. If that doesn't work i'll just get some files if i can, if not i have a back-up from last week, ill just wipe the drive and re-install windows and ubuntu. Then put everything back on.

---

### Post by vexorian on 2007-06-21
you might try using the live-cd to reformat the partition you used before to install ubuntu and install again over there, it would detect your windows partition and set the dual boot correctly. As long as the error doesn't repeat.

---

### Post by ScottY_ on 2007-06-21
The ubuntu artion is on there still, but /boot/grub doesn't exist :S

Where in ubuntu can i find reformat?

---

### Post by alienexplorers on 2007-06-21
It is called gparted.  You start it in terminal as sudo gparted.

---

### Post by ScottY_ on 2007-06-21
Interesting i only see one whole empty hard drive, all unallocated, but the files are on the drive ??

---

### Post by Thomar on 2007-06-21
I had something similar happen when I first installed Ubuntu.  The installer froze half-way through, and it hadn't installed grub so I couldn't boot at all.  I just rebooted and reinstalled Ubuntu, and everything worked fine, I can dual-boot with WindowsXP now.  Man, that was a hectic night.

Because BIOS runs before GRUB, I can hit DEL or F12 when starting up to change underlying computer settings, like forcing the computer to boot from CDROM before disk (and I'm surprised you can't do that to fix your problem).

---

### Post by ScottY_ on 2007-06-21
I can boot from CD, but i can't boot into windows, it's all on one hard drive and grub won't allow me to even choose a operating system. I'm just going to save as many files to a external drive, then wipe and reinstall windows and ubuntu. Can't be bothered to sit and sort it out.

---

