---
title: "Powerbook Titanium DVI / 867 MHz PPC - Booting"
date: 2009-03-26
forum: Apple Hardware Users
---

### Post by hirnsaege on 2009-03-26
Hello,

mentioned Powerbook is driving me insane!
I think I tried just about every method (except for Bootp, which isn't going to work) to just get an installer running on this thing. 
The DVD drive was broken, so I replaced it, hoping I could then boot an install CD and use the laptop for Unix. So, since FreeBSD-ppc won't work, I tried an old Fedora Core DVD that was lying around (PPC Version, of course). When that didn't work, either, I decided to try Ubuntu, which, of course, doesn't work.

Methods I tried:
+ Booting from the internal drive:
  - Pressing C at boottime - the drive spins up that's it, booting goes on as normal (from hd) 
  - Booting CD from OpenFirmware promt which results in either
  - - a grey screen with a barred circle in the middle (it's so sad, but this looks most promising to me)
  - - "MAC-PARTS: specified partition is not valid can't OPEN: mac-io/ata-3@20000/@1:3,\\:tbxi" (which, I think, means, no boot loader found)
  - - "LOAD size too small"
  - Pressing alt while booting - the disk shows up, selecting it as the boot device flashes a grey screen and brings me back to the menu (seems to be a common problem)
  - Selecting the disk as boot volume in OSX doesn't work at all, it won't even show up.

+ Booting from firewire CD drive: All in all about the same as above

+ Copying the loader onto an OSX partition, loading it from there: Didn't work, I think it was Load size too small.

+ Booting up in Firewire taget mode, erasing the whole disk, making a new partition and copying the contents of the cd image on there: leaves me with "specified partition is not valid"

I tried booting from CD using the above mentioned OSes, the firewire target mode thing I tried only with Ubuntu.

I also zapped the PRAM to see if it did anything. It didn't.

One thing I noticed: Using an Ubuntu CD burned w/ Disk Utility at high speed results in "LOAD size too small", same image burned w/ Toast 10 at low speed results in "Partition not valid".

Only to get this out of the way, the disk drive is working, OSX 10.5 Install DVD will boot just fine at the first attempt.

So, this is where I am now, and it sucks.
This can't be that hard, can it?

Maybe someone has any info on the above mentioned errors? Help, please!

---

### Post by truerobotech on 2009-03-26
Nothing specific on the errors but you might be in the same boat as me. I have a 667 Ti Book with very similar install woes.

So far the only sure fire way for we was to use 7.10 gutsy live cd.

Then upgrade, release by release.

---

### Post by hirnsaege on 2009-03-26
Little by little I'm getting forward.

Playing with FreeBSD-ppc loader helped me to find out why it didn't work so far. This [link](http://lists.freebsd.org/pipermail/freebsd-ppc/2004-March/000472.html) has helped me to get the booting process to work. 
Being able to load the FreeBSD boot loader from the internal HD, I played around and found out, that the CD drive doesn't respond correctly when being referred to as "cd:," it does when I call it "ide1:" tough.

So, by trial and error, I found this:

```

0 > boot cd:,\\:tbxi
 can't OPEN: cd:,\\:tbxi
 ok

```

```

0 > boot cd0:,\\:tbxi
 MAC-PARTS: specified partition is not valid can't OPEN: mac-io/ata-3@20000/@1:3,\\:tbxi
 ok

```

```

0 > boot ide1:,\\:tbxi
 can't OPEN: cd:,\install\yaboot
 ok

```

This means, that using ide1, OpenFirmware could at least see the data on the disk, which is great improvement.

So, using devalias I compared which nodes the device aliases were linked to, and i discovered, that *ide1* wasn't linked to the same node as *cd*, but that a device called *zip* was! The name of the dev node is, btw, */pci@f2000000/mac-io@17/ata3@20000/disk@0*

Consequence:
```

0 > boot ide1:,\install\yaboot

```

Launches yaboot and the installer, which, subsequently fails to find a suitable cdrom drive. Looking around in /dev yield any results.

```

0 > boot zip:,\\:tbxi
 load size=73f adler32=80dda6b0
 parsing <CHRP-BOOT>
 evaluating <BOOT-SCRIPT>

```

Seems to freeze the computer. I'll play around some more, this has given me motivation to do so.

Maybe someone already experienced the thing with the missing cd device?

---

### Post by hirnsaege on 2009-03-26
When booting the installer in expert mode I noticed the internal cd drive is being found as device hdd, yet it's not to be found in /dev.

I also tried remapping the OpenFirmware device alias of cd: to the node, which only works temporarily (until reboot). Storing the change to NVRAM using nvalias also didn't persist a reboot, and besides, it didn't fix the drive detection. Wouldn't be surprised if the NVRAM battery (if there even is such a thing) is dead, I don't know...

For now, I just went with a firewire drive, using one cd to boot (internal) and one cd to get the files off (external). The external drive got recognized immediately, and the software install is now at 85%, so I'm thinking positively. Hope, I won't be disappointed.

Anyway, this is pretty messed up. I hope getting things to work when this machine is finally set up won't be nearly as much trouble, else I see myself crawling back to the stylo monopolist's os in no time.

I'll report back.

---

### Post by truerobotech on 2009-03-26
well hirnsaege hope you install woes are over, I spoke to soon my 7.10 install went south. Finally figured out the heat buidling up in the logic board eventually causes some sort of mis-read with the cd drive.

Pop off the bottom cover turn it on its side put a fan on it and the install is in progress. Seems the board is staying cooler see if it produces positive results

---

### Post by tiresia on 2009-03-27
In such situation, if you want to install Linux in the easiest way, you should use a usb memory stick
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

Which version of Ubunt are you trying to install? Be aware that the Intrepid installer has a bug (can't detect CD-ROM), but you can boot without problems
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

In the first post, you wrote that you get the same problems with the external firewire CD-ROM, but now it looks that you can boot from it (?)
I guess, you downloaded the right version for PPC
Did you try to boot using the whole Open Firmware Path?
Please, can you post here what you get from devalias?

---

### Post by hirnsaege on 2009-03-27
Well, what do you know, now that you pointed me to that installer bug even the internal cdrom drive works like a charm!

> In the first post, you wrote that you get the same problems with the external firewire CD-ROM, but now it looks that you can boot from it (?)
Well, booting from firewire still doesn't quite work but it's not really important. I just said, I was using the internal CD drive to boot from and the firewire drive to install the files. I did this since my internal drive wasn't recognised by the installer due to the installer bug you pointed out.

The install went fine yesterday, on second attempt. Now I decided to do it over from the internal drive nevertheless, and it seems fine, it's a lot faster than from firewire, too. 

As for the output of my devalias, this is the important stuff:
```

ide1        /pci@f2000000/mac-io@17/ata3@20000/disk@1
[...]
cd          /pci@f2000000/mac-io@17/ata3@20000/disk@0
zip         /pci@f2000000/mac-io@17/ata3@20000/disk@1

```

I found out that with my mac, ide1 is the dev to talk to the cdrom drive, since talking to cd goes nowhere, I think. So, since the tbxi loader wants to load cd:,\install\yaboot i have to boot using the full path name:
```

0 > boot ide1:,\install\yaboot

```


So, booting from cd and installing seems to be sorted out. 
Now I've got one more question: how do you disable the splash screen from yaboot? I want to see the dmesg, since I think the system's hanging up while booting (from the hard disk), and I can't troubleshoot without any diagnostic messages.

---

### Post by tiresia on 2009-03-27
In the OpenFirmware as patched by Apple, you find often different alias for the same device. With the full path, I meant to choose the 'true' path (/pci@f2000000/mac-io@17/ata3@20000/disk@0)

If you don't want to see any spash image at booting, reboot after installing and edit the file /etc/yaboot.conf
```
sudo nano /etc/yaboot.conf
```
Add this line after the first block
```
append="nosplash"
```
Update the bootloader with the added option
```
sudo ybin -v
```
Restart your mac to check if it works

---

### Post by hirnsaege on 2009-03-27
I eventually tried booting using the full path, anyway, as i said, booting from the internal drive as ide1 worked seamlessly. Ubuntu's running right now.

The reason this was such a problem at first is, that I hadn't expected, and thus hadn't checked, that the cd device was being mapped wrong. After that, everything fell into place.

By the way, the reason booting the installed system didn't continue was because I had to enter the passphrase for the encrypted partitions, but there was no prompt indicating this. When I disabled the splash screen I was able to see that there was such a prompt, and after entering the passphrase everything went smooth.

Thank you, everyone. I think I can mark this one as solved. I will be back, tough.

---

### Post by degoodwin on 2010-02-26
Don't know if anyone is still interested in how to install FreeBSD on a ppc mac

In order to the disk labeler to recognize the disk you need to pre-partition it

one of the posters mention reformatting the drive in firewire target disk mode. That will work
but make sure you create one partition that stays in mac hfs format to host the loader file from /boot on the FreeBSD installation cd.
make sure you note the slice number of this partition
mine is ad0s10

Then create five more partition for  /, swap, /var, /tmp, and /usr
make sure each of these partitions is an integral multiple of 512

when you get into sysinstal , and then to the disk labeler
you should see a list of partitions. The mac partitioning method creates a number of very small driver partitions. Ignore these, leave the hfs partition untouched (you should have left a copy of /boot/loader here -- only loader itself, the rest of /boot is not needed here)

note carefully the slice number of your / partition.. mine is ad0s12 for /
/   doesn't need a great deal of space, 5 or 10 gig if you have a largish drive
swap  --- twice your RAM value
/var can be a little smaller than / or the same size
/tmp  about half of /
/usr  gets the remaining space on the disk

once you've done that

Boot from the freebsd cd (press c at boot)

at the elf prompt press a key before it boots if you are trying to install FSB 8
on my iMac G3 I had to use the following line to get it to boot into the installer
set hint.pcib.2.skipslot=14

when the install completes
add the above hint to /boot/device.hints as
hint.pcib.2.skipslot=14

also for booting to freebsd after its installed
if you took the precaution of saving a copy of /boot/loader to the root of the hfs partition

Then boot into open firmware (cmd - o -f)
you can get it to boot always to open firmware by typing 
set auto-boot?=false
then to boot into freebsd
using the slice numbers previously recorded

boot hd:hfsslice#,\loader hd:fbsdslice#
on mine
boot hd:10,\loader hd:12

the problem I am having is in loading xorg
seems to kill the btree on my /usr slice near the end of the install
I've tried over 5 times with the same result

---

