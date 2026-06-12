---
title: "Xubuntu won't install on old computer."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by gagelle on 2007-05-31
Hello,

I tried to install Xubuntu on an old computer with no success. I already checked and the computer meets the minimum requirements for memory. I think the problem is that the cd drive can't read the cd which was burnt on a newer computer. When I tried to boot to Xubuntu on the old computer, I got numerous error messages and then a final lock-up. I did a disk test, which indicated that there is an error on the disk. However, the disk works fine on two other computers which show no disk errors. This is why I think that the old cd-rom can't read the disk. I've already tried burning several other cds using the slowest speed with no luck. I also tested the iso file's checksum. I used Infrarecorder to burn the disk.

I'm already running Windows XP on the old computer which is a bit slow, but still usable. I'm going to try to swap in a newer cd-rom. I have an extra one that i don't use. It would be easier if there were another way to install the program. Is there any way to install without booting from a CD? Thanks.

---

### Post by pbw on 2007-05-31
With an existing linux install you can mount the iso image and boot from grub/lilo. I know nothing about alternative bootloaders though, but it's probably possible as well.

---

### Post by candtalan on 2007-05-31
Sometimes a CD (lens) cleaner can work ok.

Trying a different CD drive sounds like a good move.

Do you get errors from the CD drive from CDs burned elsewhere ? from other people or bought (data) CDs? If not, then:

A roundabout method would also be to try a shipit CD (professional burn) to install ubuntu fully with updates, then install xubuntu-desktop (then uninstall ubuntu-desktop).
I have done something similar, for different reasons though.
It *is* a slightlty tedious approach, because the machine was slow, but I had plenty of time.
good luck

---

### Post by poppers1957 on 2007-05-31
Try a different CD drive.  Or burn your Ubuntu distro on the slowest speed possible for your burner.  Did you check the CD for errors on the other machines that it worked on?  One little error could cause it to not work on other machines.  Was the sha1sum correct for your ISO file?

---

### Post by ske1fr on 2007-05-31
If there's a disk error on your burned disk then I'm not surprised it failed.  Always run an MD5 check on the downloaded iso file before you waste a blank CD-R on it. Try a different brand of CD-R.  Make sure you start with "noapic nolapic acpi=off" in the boot command string for old hardware.

---

### Post by gagelle on 2007-05-31
Thank you for all the advice. Yes, I already checked the iso file with Winmd5sum. I burnt the disk on a new HP notebook and it worked on that machine and also on an older Dell computer. But it won't work on the very old HP computer. It was given to me, but I think it was purchased in 2000. The cd Rom drive is read only. (Its that old!) I was able to use it to install Win XP last year and it plays music cds--just won't read the CD I burnt. I will try a lens cleaner and a different brand CD. I already used the slowest speed to burn. 

I'm completely new at this and don't know anything about the boot command string or how to change it. Is this something that's part of the ISO file?

---

### Post by Pointswest on 2007-06-04
I tried loading Xubuntu 7.04 on  a 556 Celeron w/128 ram.  The first thing I had to do was unplug the 3 1/2 drive before loading the live CD or it would hang up.  Tried many times to load program with no luck.  Added another chip of ram to increase to 196Mb and program installed just fine.  I still have problems with a slow boot but the OS is up and running on this small computer.  I have also installed Ubuntu 7.04 on an old dell 665Mz w/256Mb ram.  I think the extra ram is the key.  The specs say the OS runs on 128 Mb for the Xubuntu 7.04 release but I think it takes a little more to load it up.


Hope this might help

---

### Post by zvacet on 2007-06-04
If you are low in RAM try Xubuntu alternate CD.

[http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

And of course chek disc for errors and burn it slow.

---

### Post by pappapump on 2007-06-04
You'll get nowhere fast with that old sony y2k CD reader.
It was a standard hardware item on a lot of the HP models and is most likely the proprietary model.
Which means that it depends entirely on bios to even init.
A new CDROM is definitely a cure for your woes, and at less than $30 in most stores a CD Reader is a cheap fix.
I sell my generic CD readers for $18.00, they never sell but they look good hehe!

---

### Post by dan171717 on 2007-07-16
> **pappapump said:**
> You'll get nowhere fast with that old sony y2k CD reader.
It was a standard hardware item on a lot of the HP models and is most likely the proprietary model.
Which means that it depends entirely on bios to even init.
A new CDROM is definitely a cure for your woes, and at less than $30 in most stores a CD Reader is a cheap fix.
I sell my generic CD readers for $18.00, they never sell but they look good hehe!

i have a samsung scr 3232 cdrom drive and i have tried 6 livecds and 1 alt cd and xubuntu refuses to boot of the live cd and gets to 6% on the alt cd and starts saying it is currupt i did a disk check and the computer sayed it was corrupt in a virtual on a better pc it was fine

i have a 400mhz celeron with 192 ram

what stinks about this computer is the hdd

3gig!

---

### Post by Kowalski_GT-R on 2007-07-17
> **ske1fr said:**
> Make sure you start with "noapic nolapic acpi=off" 

Hi all,

I'm triyng to get Xubuntu Alternate Install working on a 233MMX Pentium with 64Mb.
Yesterday I had GRUB error 18, but I will try again with a (much)smaller HD and see what happens.

I just wanted to know what the quoted commands do.
Are they recommended for old hardware installations?

thank you,

Andre

---

### Post by Kowalski_GT-R on 2007-07-17
oh, forgot to specify that Xubuntu Alt. is 7.04

thank you

---

