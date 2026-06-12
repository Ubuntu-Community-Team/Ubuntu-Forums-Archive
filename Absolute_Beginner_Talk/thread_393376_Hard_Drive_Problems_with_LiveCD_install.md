---
title: "Hard Drive Problems with LiveCD install"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Gilgad Drumheller on 2007-03-25
Alright, I've downloaded the herd5 iso, burned to a disk, all that.  My computer setup is:
[LIST]
[*]Asus Motherboard
[*]AMD 64 2800+
[*]Radeon x800 Pro
[*]2 HDD's, a 120gb and a 300gb
[*]Dell LCD monitor
[*]optical mouse and keyboard connected by PS/2
[/LIST]
I'm running in safe graphics mode.  I also have had problems with my PS/2 mouse, and found that disabling usb through the bios fixed it (though i wouldn't call it a fix, i figured i'd try fixing it again once i have it installed.

Now i've got the liveCD up and running.  However, my hard drive is not recognized.  I have left 10gb on my main hard drive (the 120gb one) free for a second OS.  I do not expect the liveCD to mount the ntfs formated windows partition, but i don't think it even knows that either hard drive exists.  Case in point: when i go through the installer, the "Select a disk" dialoge shows no hard disks, and manually partitioning just affords a blank screen.
Is there any command line utility that will show me connected hard drives.

I have both drives connected by SATA, and i'm quite confident my RAID chips are disabled.  Is it possible that disabling usb support in the bios interferes with SATA.  I can't imagine.

---

### Post by finer recliner on 2007-03-25
in a terminal type:

sudo fdisk -l

and copy & paste the output here

---

### Post by Gilgad Drumheller on 2007-03-25
Alright, the output was blank.  I just went down to the next line, whre i can type in another command.
Rooting around a bit more, i see that inside /dev, there is a file called hda, but no sd_.  And when i open gparted, no devices show up (the whole bottom part is greyed out)

---

### Post by Gilgad Drumheller on 2007-04-01
Here is my /etc/fstab:
```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nouid,nodev 0 0
```
These seem to be the ramdrives set up by the LiveCD.

---

### Post by jonsimard on 2008-02-29
I have the same problem when I'm trying to install Ubuntu 7.10 in safe graphic mode.

The only difference is that I can see my IDE drive. But my SATA, nothing...

I need that SATA drive for my setup.

---

### Post by Gilgad Drumheller on 2008-03-01
I'm relatively sure that my problem was fixed by using the newest Ubuntu release, rather than the beta Herd 5.

However, it would seem that you are already doing that.  Sorry I cannot provide more of a solution, this was a long while ago.

---

