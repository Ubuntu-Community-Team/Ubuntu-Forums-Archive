---
title: "My Key Drive"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-11-23
I am in need of some help...

I have recently put linux in my PC aswell as Windows...

I had a key drive that worked perfectly in Windows, and I decided to put some files on it in Linux...but now when I view it in Windows it displays no files and It says the Key Drive's size is 0 bytes, I have tried to re-format it in windows, but It didn't work...

But in linux it works perfectly, how can I make it work in Linux and Windows XP....

I don't mind deleting files if nessacery

Thanks for your help

---

### Post by Kapre on 2005-11-23
[QUOTE=lavarock09]I am in need of some help...

I have recently put linux in my PC aswell as Windows...

I had a key drive that worked perfectly in Windows, and I decided to put some files on it in Linux...but now when I view it in Windows it displays no files and It says the Key Drive's size is 0 bytes, I have tried to re-format it in windows, but It didn't work...

But in linux it works perfectly, how can I make it work in Linux and Windows XP....

I don't mind deleting files if nessacery

Thanks for your help[/QUOTE]

lavarock - Are you using Ubuntu? I also have a keydrive and am using it sharing files between my Ubuntu/Fedora and M$ and everything seems fine. I just put it in and it just shares (docs, MP3) If I may, what kind of files (from Linux) did you load on it.I hope you did not load the DSL (Damn Small Linux) OS on it.

K

---

### Post by lavarock09 on 2005-11-23
1. I am using Ubuntu aswell as WIndows XP

2. I didn't put Damn small linux on it...

But at the moment I think I have completely trashed it...

I was using the 'Disks' tool in Ubuntu and I change the disk type on it to Swap, and now I can't change it again, and It still wont work in Windows or Ubuntu

---

### Post by Brunellus on 2005-11-23
lavarock:  you have misunderstood the meaning of "swap"

"swap" is scratch space, roughly equivalent to windows virtual memory.  the linux kernel uses an unformatted partition designated as "swap" to supplement your physical RAM.

Essentially, you wiped whatever formatting was on the USB drive when you made it swap.  To make it useable again in both Windows and Linux, you must format it again, but as FAT32.

---

### Post by lavarock09 on 2005-11-23
[QUOTE=Brunellus]lavarock:  you have misunderstood the meaning of "swap"

"swap" is scratch space, roughly equivalent to windows virtual memory.  the linux kernel uses an unformatted partition designated as "swap" to supplement your physical RAM.

Essentially, you wiped whatever formatting was on the USB drive when you made it swap.  To make it useable again in both Windows and Linux, you must format it again, but as FAT32.[/QUOTE]

I understand that, but only after I had done it...

So you might be able to help...

When I try to format it in Windows, it does nothing...

And It wont let me do it in Ubuntu anymore, unless I can do it through Terminal

---

### Post by d1337 on 2005-11-23
I'm just taking a stab in the dark, but have you tried to access it through System --> Administrations --> Disks?  There are some options there that may allow you to format that drive if you are able to see it.  Methinks it would use a vfat filesystem...but again, I'm just taking a stab.

d1337

---

### Post by jfryman on 2005-11-23
[QUOTE=lavarock09]I understand that, but only after I had done it...

So you might be able to help...

When I try to format it in Windows, it does nothing...

And It wont let me do it in Ubuntu anymore, unless I can do it through Terminal[/QUOTE]

Easy to fix. You'll need to know the device of your USB key (usually sda, unless you have other SCSI devices attached). If you're not sure, run this command after you insert your key..
```

$ dmesg

```
and look for lines that resemble the following... should be at the bottom
```

[4298106.331000] USB Mass Storage support registered.
[4298111.336000]   Vendor: LEXAR     Model: JUMPDRIVE ELITE   Rev: 1000
[4298111.336000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4298111.347000] usb-storage: device scan complete
[4298111.545000] SCSI device sda: 248928 512-byte hdwr sectors (127 MB)
[4298111.552000] sda: Write Protect is off
[4298111.552000] sda: Mode Sense: 43 00 00 00
[4298111.552000] sda: assuming drive cache: write through
[4298111.578000] SCSI device sda: 248928 512-byte hdwr sectors (127 MB)
[4298111.585000] sda: Write Protect is off
[4298111.585000] sda: Mode Sense: 43 00 00 00
[4298111.585000] sda: assuming drive cache: write through
[4298111.585000]  sda: **sda1**
[4298111.645000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

```

For example, my key is /dev/sda1. Now you want to format the sucker. Open up your terminal, and type the following.
```

$ sudo mkfs.vfat -n <volume_name> /dev/<key_device>

EXAMPLE:
$ sudo mkfs.vfat -n USBKey /dev/sda1

```

where <volume_name> is the name you want to assign to the drive (arbitrary... does not matter... call it SesameStreet if you want. :) ) and <key_device> is the device of the key, as recgonized by the kernel.

From there, you can remove the key and re-insert it, and the automounter should pick it back up. Also should work in Windows!

Good luck!

-James

---

