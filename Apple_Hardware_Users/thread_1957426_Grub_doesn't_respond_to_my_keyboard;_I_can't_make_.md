---
title: "Grub doesn't respond to my keyboard; I can't make a selection - MacBook"
date: 2012-04-12
forum: Apple Hardware Users
---

### Post by namkcuR on 2012-04-12
Hello, first post here, seems like a nice community you have here.

My setup is as follows:

I am on a 2007 Macbook - not MBP, just Macbook.

Its internal HD is a 750GB Seagate Momentus, with only one partition, on which OS X Snow Leopard is installed.

I have a 40GB external USB hard drive with two(so far) partitions on it - one is Ubuntu 10.10, the other is Kubuntu 10.10(I know they're not up-to-date versions, but those are the CDs I already had, and I don't think my problem will have much if anything to do with OS versions).

I should mention that refit doesn't seem like huge hard drives like my internal 750GB Seagate, and because of that, it simply won't work, so I can't use that as a means of booting from USB.  Instead, I am using Plop Boot Manager, which is burned on a CD.  

So, I boot from the CD, the Plop Boot Manager starts, and I select 'USB' from its boot menu, upon which GRUB loads.

Here's the problem:  GRUB doesn't respond to my keyboard.  I can't change the selection with the arrow keys, I can't press c to go to a command prompt, nothing.  So, the timer gets to zero and the default selection(Kubuntu, since it was installed last) boots up(with no additional problems, I should add).  

At first I thought GRUB was just having a problem recognizing the Macbook's internal keyboard, so I plugged an external USB keyboard in, but GRUB didn't respond to that either(that's why this isn't in the Apple section, I'm not 100% sure it's a Macbook issue).

I've googled around and it seems like I'm not the only one who's had this issue, but I haven't been able to find a solution.  I know I could simply change the default OS to load in the grub configuration file, and that would enable grub to boot something other than Kubuntu, but that's a workaround.

Does anyone have any idea what the problem is?  Thanks in advance, I appreciate it.

---

### Post by oldfred on 2012-04-12
Welcome to the forums.

I will  move your thread to the Apple sub forum as those who know Macs may be able to help.

In Windows it is usually a BIOS setting to turn on USB keyboard & mouse. Both Windows and Ubuntu use drivers that bypass BIOS, but grub seems to use BIOS. 
But your Apple has UEFI(?), so I do not know what settings you may have.

---

### Post by namkcuR on 2012-04-12
It's not just the usb keyboard though, grub doesn't recognize the MacBook keyboard either.

Regarding BIOS vs EFI, ubuntu and kubuntu install grub-pc by default, but there's also a grub-efi package.  I installed grub-efi, but grub still didn't recognize the MacBook keyboard, so I removed grub-efi and re-installed grub-pc.

Trying to think of other things to try.

---

### Post by oldfred on 2012-04-12
This has some info on Mac as well as non-Mac UEFI booting.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

---

### Post by God of the Meeps on 2012-04-13
I had the same problem with Legacy GRUB. Upgrading to GRUB2 fixed the problem as far as I can tell.

---

