---
title: "Apparently successful Installation failed"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by jowiggs on 2008-03-28
This must be an oft recurring thread, sorry but I can't find one that answers my question, and I don't want to spend 3 hours reading every thread that may be similar.

So: Total newbie to Linux...

Read instructions to install Ubuntu alongside existing windowsXP. Did quite a bit of reading around it to make sure I didn't do anything silly.

Left a nice big partition for it, live CD (Ubuntu 7.10 AMD64) runs fine (trouble configuring the wireless internet which I understand is a headache and will therefore leave until I've got a harddrive installation), graphical installer works fine, right to the end. System shuts down, disk ejected, no problems.
System starts up again, no boot loader. I fixed this by installing GAG, which worked fine. It now loads WinXP no probs, but tells me that the linux doesn't have a working bootloader.

So, where now? Different Linux distro?

thanks for any help,

Jo

---

### Post by cisforcojo on 2008-03-28
Can you describe what you mean by "no bootloader"?
Are there any errors? I've had some problems with that before and might be able to help.

---

### Post by northern lights on 2008-03-28
GRUB apparently didn't get installed after the Ubuntu setup - were you not prompted to install GRUB? 

If so, you could choose to setup again, this time with GRUB.

If not, you could boot with the live CD and install it from [here]("http://www.gnu.org/software/grub/grub-2-download.en.html")

---

### Post by billgoldberg on 2008-03-28
Different distro?

It's just a boot problem.

Download the super grub disk live cd (google).

Burn it to disk.

Using that boot your linux partition.

In you linux partition install grub and add your windows partition.

---

### Post by jowiggs on 2008-03-28
Thanks.

I'm posting this from work, which means that I can't see the actual output. I will try to put more details on this weekend.

I've actually tried this twice - the second time I took the installation a lot slower, and at some point on the installation wizard I clicked an "Advanced" button, which brought up a dialogue with an "install GRUB" check-box, which I made sure was checked before closing. As far as I know it was instructed to install GRUB.

I thought GAG *was* an alternate bootloader. I will try Super Grub instead.

Cheers!

Jo

---

### Post by northern lights on 2008-03-28
The super grub disc still installs GRUB - it's simply another Live CD equipped with the means to setup GRUB...

---

### Post by jowiggs on 2008-04-01
Hi!

OK, have tried SuperGrub. It installed fine, recognised WinXP in the first partition and Ubuntu 7.10 in the third and fourth partitions (second is a FAT32 documents share partition). I told it to fix the linux grub installation, which it said it did.

However, it flags an error when I try to load Ubuntu (Error 22).

Did I fail to actually get it to save grub in the linux partition?

thanks,

Jo

---

### Post by northern lights on 2008-04-01
Windows boots now, right?!

You could try running
```
fdisk /mbr
```
from the Windows commandline in hope that that might fix the issue.

Further, check out
[How To fix grub from the Live CD]("http://ubuntuforums.org/showthread.php?t=22435")

---

### Post by bumanie on 2008-04-01
Could you post the output of 
> sudo gedit /boot/grub/menu.lst and 
> sudo fdisk-lu
That will help us identify exactly which drive is which and where grub should be. It looks as though grub is pointing to the wrong partition.

---

### Post by jowiggs on 2008-04-02
Should I enter these commands from the Ubuntu live CD, or from the Super grub cd?

---

### Post by northern lights on 2008-04-03
It doesn't matter, you could use any distribution's Live CD, theoretically.

Your comp & a commandline is all you need...

---

### Post by jowiggs on 2008-04-06
menu.lst seems to be an empty file.

output from "sudo fdisk -lu" command:

[INDENT]
Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39337a2e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   234468674   117234306    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3a303a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS
/dev/sda2       156296385   221825519    32764567+   c  W95 FAT32 (LBA)
/dev/sda3       221825520   308769299    43471890   83  Linux
/dev/sda4       308769300   312576704     1903702+   5  Extended
/dev/sda5       308769363   312576704     1903671   82  Linux swap / Solaris

[/INDENT]

---

### Post by northern lights on 2008-04-06
mkey. Judging by the fdisk output, your "/boot/grub/menu.lst" should look something like the following. This is only valid completely however, if you're Ubuntu is Gutsy, your kernel version thus 2.6.22 and the NTFS partition does have a Windows install, as I assumed.
```
title		Ubuntu
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d8734276-0e8d-49cc-83ca-9a6137e5bc47 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d8734276-0e8d-49cc-83ca-9a6137e5bc47 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by jowiggs on 2008-04-07
Great, thanks - I will try that.

Looking closely at the output, it seems to be treating my other hard drive, an IDE, as the first one, with the OSs installed on the other drive. Could this be the cause of my woes?

Cheers

Jo

---

### Post by northern lights on 2008-04-08
> **jowiggs said:**
> it seems to be treating my other hard drive, an IDE, as the first one
Darn.That's true. It does not necessarily render my above post completely useless, but it's certainly false.

For once, you're right, the IDE drive comes first in the order*. Thus, in GRUB syntax, the Linux is on (hd1,2) and Windows on (hd1,0). The Linux shouldn't care where it resides. Windows wants to be on the first harddrive though.

I believe you got two options. You could setup a fresh Windows on the first partition of the IDE drive. Maybe make it master also, and run Windows from hda1 / (hd0,0). Or you could remap drives in GRUB. For that google or check [this entry in the GRUB manual]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows") or [this article on LinuxSelfHelp]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html")


* In a machine with a full IDE and a full SATA controller, the drive order would be hda, hdb, hdc, hdd, sda, sdb, sdc, sdd. Where hd* are the IDE drives and sd* the SATA ones. The suffix describes the physical setup in the comp - a is the primary master, b the primary slave, and so on.

---

### Post by jowiggs on 2008-04-08
> **northern lights said:**
> The Linux shouldn't care where it resides. Windows wants to be on the first harddrive though.

Interesting, that, as Windows was installed without the IDE in place, the IDE was added later but Windows continued to work fine. Linux, on the other hand, was installed with the IDE in place...

Could I reinstall GRUB after removing the IDE, and then replace the IDE?

I will look at remapping drives, it may be easier in the long term if the computer permenantly treats the IDE as the second drive, as it's an older, slower drive and I don't want any OSs on it.

---

### Post by jowiggs on 2008-04-28
Hi!

As Hardy Heron was out, I tried installing Wubi 8.04 to see if that works...
It does, and rather oddly, it also allows me to successfully start the original 7.10 installation!
A number of questions - would someone be so kind as to answer them for me please:

I have a AMD64 PC with 32bit Windows XP installed (Also Wubi8.04 and Ubuntu7.10!). I wanted to port to Ubuntu for the following reasons:
[LIST]
[*]I like the concept of Open Source software, I use it on Windows for preference
[*]I don't want to upgrade to Windows Vista, and my existing copy of XP is getting old
[*]I would like to run a 64 bit system
[*]There are still a number of programs that I would like to use that are only available for Linux
[/LIST]
However, I am as yet fairly reliant on WinXP for a lot of things and want to take a year or two before I can decide to entirely move over.

In view of that:
[LIST=1]
[*]Is Wubi a good idea for installation until I am ready to ditch Windows altogether?
[*]Is there any reason *not* to install Wubi (and give up with the full installation that has given me headaches)?
[*]Is Wubi 64bit? Even installed through a 32bit Windows platform? How can I check?
[*]I made a FAT32 documents partition because I was led to understand that Linux won't write to NTFS. How can this be true if Wubi installs on NTFS? While I've got two systems I want to be able to use NTFS because WinXP won't recognise anything decent and FAT32 is woefully aged, so it would be great if I can just keep with NTFS for now.
[*]Why on earth did other grub-based bootloaders not cope with my set-up but Wubi does (it loads Windows, Separate Ubuntu 7.10 *and* Wubi Ubuntu 8.04 no trouble)?
[/LIST]

Thanks very much...

---

### Post by jowiggs on 2008-04-29
Should I be re-posting this on the new newbie forum?...

---

