---
title: "help!!! using ubuntu live CD to fix MBR if possible"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-09-20
Hi,

I use ubuntu on my regular machine.  However, I am working on a machine that has CentOS (redhat) installed with GRUB.  I need to get windows XP installed on it instead.  Booting from the regular windows install CD comes up with a blank screen.  After searching around forums I have found this info that I want to try:

>  to get the XP install CD to work, need to boot into linux with a linux rescue CD, then DON'T mount the hard drive, then zero out the MBR like this:

dd if=/dev/zero of=/dev/hda bs=512 count=1

Then reboot with the XP install CD and install XP.

Can I do this with the Ubuntu live cd?  I do not have a floppy drive on the machine.  Also, I am very new to linux, so hopefully this doesn't get crazy complicated.  :sad: 

I'm pretty sure if I get rid of GRUB everything will be OK.

---

### Post by gn2 on 2006-09-20
Would it perhaps be easier to remove the offending computer's hard drive, then put it in another PC as slave, or in an external USB enclosure and completely delete the partition(s)?

That would allow the windows disc to create a partition in the unallocated space before installing?

---

### Post by bulldog on 2006-09-20
If I understand correctly,you boot from the windows cd.
And this won't work?

As far as I know is booting and installing windows from the windows cd a peace of cake.

By booting from cd GRUB will not load,and can't do anything.

It overwrites GRUB with is own bootloader and you can format the drive NTFS to remove your distro.

Than just install windows and evrything should be as expected.

---

### Post by k9brand on 2006-09-20
hmm.. yeah that's exactly what I thought too, but it doesn't even get that far to install windows.  It says:

"press any key to boot from CD.." 

Then when I do that, the screen turns blank.  I have tried 2 different XP home discs and 1 XP pro disc (all real, not burned) with the same results.

I'll try taking the HD out and reformatting....

Quick question though, can't I just use FDISK on the live CD ?

---

### Post by bulldog on 2006-09-20
Yep should be possible to use gparted or what ever you want,but you have to umount the drive before your changes can be done.

---

### Post by bigken on 2006-09-20
sounds like a bad cd/dvd/player to me have you tried  any other boot discs ? other than windows

---

### Post by Kilz on 2006-09-20
You could also get a windows98 boot disk, [images are avilable]("http://www.bootdisk.com/"). put the floppy in and boot it. Then type in ```
fdisk /mbr 
``` at the prompt.

---

### Post by PietreWitobi on 2006-09-20
Sorry, Nevermind.

---

### Post by k9brand on 2006-09-20
Kilz, thanks.  That worked for me.

I'm glad it's not my computer, I like my ubuntu :)

---

### Post by xpod on 2006-09-20
> I need to get windows XP installed on it instead

MY sympathy to the afflicted:D

---

### Post by Kilz on 2006-09-20
> **k9brand said:**
> Kilz, thanks.  That worked for me.

I'm glad it's not my computer, I like my ubuntu :)

Your welcome, its something I remembered from my old windows days. Whoever wants to remove Linux, its their loss. But some folks are happy running the bug infested slow security flaw from Microsoft.  :D

---

