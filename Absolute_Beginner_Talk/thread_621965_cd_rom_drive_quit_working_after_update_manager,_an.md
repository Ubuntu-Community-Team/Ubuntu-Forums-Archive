---
title: "cd rom drive quit working after update manager, any thoughts?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by foytix on 2007-11-24
SOLVED

sorry for the n00b type ? up until i let the update manager install updates (all 86 of them) my cd rom drive was working fine.  now for some reason the drive won't even acknowledge  that a cd is in the drive let alone read it.  i'm pretty new to the ubuntu community but i did a few searches and couldn't come up with anything concrete.  Thanks in advance.
ps the drive isn't bad i can still boot off of the live cd and and the cd's work in windums on the dual boot ( soon to be gone when i work the kinks out of 7.10 )

---

### Post by Pumalite on 2007-11-24
Check /dev and see if you still have a cdrom device there.

---

### Post by philinux on 2007-11-24
Post the output of this 

```
cat /etc/fstab
```

---

### Post by foytix on 2007-11-24
not sure how to check /dev (n00b) ps how do i check /dev?
when i asked for this list there was a cd in the drive (also it's not a burner so i'm not sure i this line is bunk or not)

jeremy@jeremy-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives
gnome-mount 0.6

** (gnome-mount:6899): WARNING **: Drive /dev/scd0 does not contain media.
Drive:
  name:                 CD-ROM GCR-8480B
  device:               /dev/scd0
  door:                 closed
  type:                 CD
  is mounted:           FALSE
  max read speed:       8448 KiB/s (CD 56.3x, DVD 6.2x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined

---

### Post by Pumalite on 2007-11-24
post:
cat /etc/fstab
(you should have something similar to this in the file:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0)

---

### Post by foytix on 2007-11-24
thanks this is what i'm looking at

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=32b0f4d8-524a-4541-bc7d-1b42a37425d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=01268bac-d193-4ae1-b55b-9d938e32a47f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by foytix on 2007-11-24
Philinux sorry i missed your post here's what i get from your suggestion

jeremy@jeremy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=32b0f4d8-524a-4541-bc7d-1b42a37425d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=01268bac-d193-4ae1-b55b-9d938e32a47f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
jeremy@jeremy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=32b0f4d8-524a-4541-bc7d-1b42a37425d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=01268bac-d193-4ae1-b55b-9d938e32a47f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by philinux on 2007-11-24
Well this looks just fine.
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Exactly the same as mine.

---

### Post by philinux on 2007-11-24
This is what the first bit of my /dev directory looks like

---

### Post by Pumalite on 2007-11-24
Time to check your BIOS. What BIOS and motherboard do you have?

---

### Post by foytix on 2007-11-24
well like i said the cd drive works fine outside of ubuntu 7.10 but i'm running an IBM NetVista with IBM Net Bios and ACPI Uniprocessor PC with a P4 at 1.8ghz

---

### Post by Pumalite on 2007-11-24
Get in your BIOS and report back all the possibilities of configuration for CD-Drive and what is it set to now? 'Esc', 'Del', or 'tab' many times are the keys to get into BIOS. Consult your Manual if you don't know it.

---

### Post by foytix on 2007-11-24
alright in the bios for the IDE Drives i have

IDE Drive 0    40016 MB
IDE Drive 1    Not Installed
IDE Drive 2    CD/DVD-ROM
IDE Drive 3    Not Installed

under IDE Drive 2
type     [CD/DVD-ROM]
IDE Performance      [High Performance]          compatible is the other option
IDE Read Prefetch     [Disabled]             enabled is other option

---

### Post by Pumalite on 2007-11-24
Try 'compatible'

---

### Post by runemaste644 on 2007-11-24
Can you list the updates you did? Did it tell you to reboot after those updates?

---

### Post by foytix on 2007-11-24
alright i tried compatible no good
then i tried compatible and enabled no good
then i tried high performance and enabled no good
put back to like it was originally

ps leaving work will resume monday
home to try to fix ubuntu on home desktop and laptop two completely different issues from this

thanks again

---

### Post by foytix on 2007-11-27
how can i find out which updates were loaded and can i reverse them.  i don't think it required me to restart the computer afterwards, but it's been restarted many times since.  this is a work computer and i need to get the cd drive working, thanks

---

### Post by foytix on 2007-11-27
well i switched to lilo vs. grub for my boot as i read this had cured some peoples problems, but it didn't help me so i switched back to grub.  

Does anyone have any thoughts about what this could be?  i'm not finding anything that works.
thanks

---

### Post by foytix on 2007-11-27
Solved

Had to run a patch for hal-0.5.9.1  listed as bug#109763 in hal
as soon as i finished installing the patch my cd mounted ( it was quick )
here's a link to the site with info on the patch you have to scroll down a little

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109763]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109763")

thanks again to everyone who offered help.

IMPORTANT when the automatic update manager asks you install hal after this patch do NOT install, you'll have to repeat the process
i found out the hard way

---

