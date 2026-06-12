---
title: "rEFIT on Ubuntu partition"
date: 2009-04-06
forum: Apple Hardware Users
---

### Post by bludimnd on 2009-04-06
Hi guys

I installed Ubuntu on my Macbook Air's whole hard drive, thus completely (or as much as possible) removing Mac OS X. 

In order to boot into Ubuntu I use the external superdrive with a burned rEFIT CD.

Where on my HD should I install rEFIT so that I can boot without attaching my external drive each time?

Thank you for your assistance.

Kind regards

Adam

---

### Post by pxwpxw on 2009-04-06
> **bludimnd said:**
> Hi guys

I installed Ubuntu on my Macbook Air's whole hard drive, thus completely (or as much as possible) removing Mac OS X. 

In order to boot into Ubuntu I use the external superdrive with a burned rEFIT CD.

Where on my HD should I install rEFIT so that I can boot without attaching my external drive each time?

Thank you for your assistance.

Kind regards

Adam

refit wont boot from a linux partition. 
Usually create a small hfsplus partition on the HD or a USB stick, install it there and then run OSX to bless it with enable-sh. Usually the HD is partitioned as a GPT disk, but can work for a MSDOS disk. However you need to run OSX (from DVD or HD or USB) to enable it.
i.e. refit cant bless itself.

---

### Post by bludimnd on 2009-04-06
> **pxwpxw said:**
> refit wont boot from a linux partition. 
Usually create a small hfsplus partition on the HD or a USB stick, install it there and then run OSX to bless it with enable-sh. Usually the HD is partitioned as a GPT disk, but can work for a MSDOS disk. However you need to run OSX (from DVD or HD or USB) to enable it.
i.e. refit cant bless itself.

Thank you for your reply. So basically once I've made the partition and installed rEFIT on it, I just need to insert the Mac*OS*X DVD, or actually install Mac OS*X and then run it? 

Either way, since my Mac OS*X DVD*is damaged it probably won't work. Any other way of blessing it? I have another Mac with Mac OS*X on it that is working, can I somehow use that?

Kind regards

Adam

---

### Post by pxwpxw on 2009-04-06
> **bludimnd said:**
> Thank you for your reply. So basically once I've made the partition and installed rEFIT on it, I just need to insert the Mac*OS*X DVD, or actually install Mac OS*X and then run it? 

Either way, since my Mac OS*X DVD*is damaged it probably won't work. Any other way of blessing it? I have another Mac with Mac OS*X on it that is working, can I somehow use that?

Kind regards

Adam

Yes you can possibly bless it from another mac using target firewire connection, if it is on a hfsplus partiton (or install  and bless on usb stick) You only need bless initially.

But it might  be possible to boot without using refit.

EDIT: In fact, you should be able to boot using the option key without refit, because refit just uses the Apple msdos compatibility mode to boot linux.

---

### Post by bludimnd on 2009-04-06
> **pxwpxw said:**
> Yes you can possibly bless it from another mac using target firewire connection, if it is on a hfsplus partiton (or install  and bless on usb stick) You only need bless initially.

But it might  be possible to boot without using refit.

EDIT: In fact, you should be able to boot using the option key without refit, because refit just uses the Apple msdos compatibility mode to boot linux.

Can I install and bless on USB*stick, then copy from USB*stick onto Linux HFSplus partition on Ubuntu?

I do not want to have to use an external drive to boot my laptop each time.

---

### Post by pxwpxw on 2009-04-06
> **bludimnd said:**
> Can I install and bless on USB*stick, then copy from USB*stick onto Linux HFSplus partition on Ubuntu?

I do not want to have to use an external drive to boot my laptop each time.

You can copy the files, but the blessing stays with the original.
You need check if you can make an hfsplus partition with gparted, hfsplus formatting  is not usually available from ubuntu (not on my ubuntu904).

Booting from a usb stick works, it can be unplugged once linux is booted.

But have you tried booting directly using the option key, without the external drive and without refit. It should work, but may take about 30 seconds to get to the Apple 'Windows' disk icon to boot that way. Thats the easy way if it works.

---

### Post by cyberdork33 on 2009-04-06
> **pxwpxw said:**
>  You need check if you can make an hfsplus partition with gparted, hfsplus formatting  is not usually available from ubuntu (not on my ubuntu904).
parted magic can.

---

### Post by bludimnd on 2009-04-08
Option key brings up wireless networks to choose. No partitions, or OS.

I didn't use Bootcamp. Could that be the problem?

---

### Post by pxwpxw on 2009-04-08
> **bludimnd said:**
> Option key brings up wireless networks to choose. No partitions, or OS.

I didn't use Bootcamp. Could that be the problem?

Oh, sorry I forgot you are on a MBAir, I need to think about that.

---

### Post by bludimnd on 2009-04-08
> **pxwpxw said:**
> Oh, sorry I forgot you are on a MBAir, I need to think about that.

How would I install rEFIT on a USB*driver? This might actually be an excellent security solution for my employees! ;)

---

### Post by pxwpxw on 2009-04-08
I think you just need to reinstall grub bootloader from ubuntu on the hard drive.

Restart and from refit, run the Partition Tool to Update the MBR, or if that has a problem stop there and report.
Restart again and from refit boot into your installed  ubuntu system.

From a terminal see if you have grub installed, (you may have grub-pc which is grub2)

This should give a grub> prompt if its grub.
```

sudo grub

```
If you get the grub prompt, do this
```

grub> find /vmlinuz

```
It should report something like (hd0,1) at a guess.
```

grub> quit

```
quit and report the result.

---

### Post by bludimnd on 2009-04-08
Grub is installed. 

I get HD0,0

When I startup rEFIT from the CDROM I first run the Partition tool and choose update the MBR. It completes successfully. 

Then when I reboot, without the Superdrive plugged in, I get the mac folder with the question mark.

I've tried this several times.

---

### Post by pxwpxw on 2009-04-08
> **bludimnd said:**
> How would I install rEFIT on a USB*driver? This might actually be an excellent security solution for my employees! ;)

Just copy the refit CD files to a hfsplus partiton on a usb stick (details should be on refit web site), although I think you might need to use a Mac with OSX installed. And refit.efi needs to be blessed using OSX.

---

### Post by pxwpxw on 2009-04-08
> **bludimnd said:**
> Grub is installed. 

I get HD0,0

When I startup rEFIT from the CDROM I first run the Partition tool and choose update the MBR. It completes successfully. 

Then when I reboot, without the Superdrive plugged in, I get the mac folder with the question mark.

I've tried this several times.

Restart again into ubuntu and see if you can finish the job with grub.

You have found that vmlinuz is on hd0,0 which is th first partition on the hard drive.
This should resinstall grub bootcode to the MBR of the HD.

```

sudo grub

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

See if that cahnges anything.

---

