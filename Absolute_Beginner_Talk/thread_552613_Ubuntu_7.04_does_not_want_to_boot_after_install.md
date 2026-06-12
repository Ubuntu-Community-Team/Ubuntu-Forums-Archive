---
title: "Ubuntu 7.04 does not want to boot after install?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by tomot on 2007-09-16
I d/led the latest Desktop Edition of Ubuntu yesterday,I then burned the image.
But after the install, when it says to remove the CD, the Ubuntu OS wont boot
from the HD ?

I have a 40 gig Seagate HD dedicated to Ubuntu which I had previously formatted under  XP
using Seagate Diskwizard. (20gig primary, the remainder logical), all formatted fat32
I also gave each partition a volume name  ,Ubuntu c, and Ubuntu d.

When I found that Ubuntu would not boot from the HD. I had installed that HD into a  secondary position on my computer,
I then booted my normal  XP HD   (thank god for removable HD trays)

Running XP I could not see the Ubuntu HD in explorer.  But under Disk Management I found the 
following:

1. the volume names were now missing
2. the primary and logical partitions had been changed by Ubuntu to 35.7gig primary 1.57 gig logical
3. both partitions have no file system showing.

I have done this install twice now, with the same result. 
except the first time I made the entire 40 gig Seagate HD primary.

---

### Post by tomot on 2007-09-16
I'm sorry for the dbl post

---

### Post by richardward101 on 2007-09-16
> **tomot said:**
> 
1. the volume names were now missing
2. the primary and logical partitions had been changed by Ubuntu to 35.7gig primary 1.57 gig logical
3. both partitions have no file system showing.


This bit specifically is normal; its just that windows doesn't understand linux partitions (unless you get a third party driver for ext2/3).
As for the not booting, do you mean it tries to boot but crashes? or do you mean that it just goes straight to the windows?
If its the latter then it sounds like GRUB (the bit that boots linux) is installed on your second hdd, but your computer looks at the first HDD before that, finds the windows boot code and runs it, so GRUB doesn't get a look in. The easiest way is probably to run the install again, and on the final screen before install you click advanced, which gives you the option of where to install GRUB, and you want to install it to the first hard disk.
Hope this helps, post back!

---

### Post by tomot on 2007-09-16
> **richardward101 said:**
> 
As for the not booting, do you mean it tries to boot but crashes? or do you mean that it just goes straight to the windows?


firstly.... thanks for your reply richard

It does not crash!
It cant boot into windows either because the bootable HD containing  XP has been removed from my computer.
It has been replaced with the 40gig HD containing Ubuntu instead.

 .... I get the  "error Loading OS " message. which comes from the  Bios .
Which  is the same message one would get if you installed an HD without an operating system on it.

I also tried using the Gnome Partition editor, thinking   it might do a better job formatting FAT 32
on my 40 gig hd, prior to installing Ubuntu

I have other HD's on my computer, but they contain data only. and I made sure that none  of them
is bieng  used accidentally for the Ubuntu install. I hope the install procedure is not inadvertently
installing GRUB on one of my NTSF data  HD's? 

I'm still looking for help :)

---

### Post by Skidpad on 2007-09-16
Lots of questions come to mind here, but can you reboot the Live cd, open a terminal, and post the output of "sudo fdisk -l"?  
That's without the quotes, and the -l is a lower case L.

Let's see what your file system/drives look like (as viewed by Ubuntu...).

edit: we can also see what we need to in the Gnome Partition Editor (GParted) - also on available once you boot the live cd.

---

### Post by tomot on 2007-09-16
I'm back at the step 7 of 7 screen in the Ubuntu gui

part of the screen read:

the following partitions  are going to be created: (this is my 40 gig HD)
partition #1 of SCSI1 (0,0,0) (sda) as ext3
partition #5 of SCSI1 (0,0,0) (sda) as  swap

the Advanced  Options screen reads:
Boot loader: device  for boot loading installation

(hd0) 

I cant find any reference within the Ubuntu gui
as to what drive this is refering to.
hence I dont know what to type into the space
to point the boot loader to my 40 gig HD.

---

### Post by tomot on 2007-09-16
skidpad, I must have been typing my last post while you were replying

I'm currently on my 2nd old celeron machine with also has access to the net
I currently have the Ubuntu install process stopped at the step 7 of 7 screen
on the other computer.

---

### Post by tomot on 2007-09-16
typing "sudo fdisk -l" into the terminal

shows 3 ntfs hd's, and one 40 gig hd 

the 40 gig hd has the following under its headings:

/dev/sda1 *  1  4865  39078081  c    W95 FAT 32 (LBA)

---

### Post by kevin11951 on 2007-09-16
ok, here are my 2 cents...

[LIST=1]
[*]Remove/Unplug All HDD Except The Ubuntu One
[*]Wipe That HDD By Installing Ubuntu The Normal Guided Way (no special partitions, just how ubuntu wants it and thats all)
[*]Then Restart, and Tell Us How That Goes
[/LIST]

---

### Post by Skidpad on 2007-09-16
^^^^ Agreed.  Do that, and then you can install GRUB as/where needed.  Let Ubuntu create it's own partitions - don't use a 3rd party program.

---

### Post by tomot on 2007-09-17
> **kevin11951 said:**
> ok, here are my 2 cents...

[LIST=1]
[*]Remove/Unplug All HDD Except The Ubuntu One
[*]Wipe That HDD By Installing Ubuntu The Normal Guided Way (no special partitions, just how ubuntu wants it and thats all)
[*]Then Restart, and Tell Us How That Goes
[/LIST]

thanks for this simple how to!

removing all the HDD's has helped the situation.
It made it easier for the Ubuntu installl procedure to its thing.

Ubuntu now boots from the HDD it was installed upon.....  :)

I reconnected 2 HDD's which are using the on board ATA 133 controller.
Ubuntu sees them in its GUI aswell. 

However! Ubuntu does NOT boot if I connect 2 other HDD's to my PROMISE -2-Channel Low-Profile PCI 32bit/66MHz ATA133 Controller card. 

Here it boots to the Ubuntu screen, then hangs when its trying to read the rest of the boot procedure
the orange loading indicator stays fixed at about 1/8" showing.
there must be some kind of address issue happening here.

any ideas?

---

### Post by diatribe on 2007-09-17
reboot with no splash and see the error message when it hangs

---

### Post by tomot on 2007-09-17
sorry...... but what do I do, to not have the splash screen showing?

---

### Post by diatribe on 2007-09-17
if you boot in recovery mode it should work, or you could edit your bootline to exlude splash and quiet

---

