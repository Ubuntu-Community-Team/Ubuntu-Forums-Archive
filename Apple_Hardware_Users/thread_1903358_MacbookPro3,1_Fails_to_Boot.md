---
title: "MacbookPro3,1 Fails to Boot"
date: 2012-01-02
forum: Apple Hardware Users
---

### Post by wiz561 on 2012-01-02
Hi!

I'm trying to install Ubuntu on my Macbook Pro 3,1.  I'm using the Oneiric amd64 alternate CD.  I've tried to install it as a 'single boot' (get rid of OSX and have ubuntu use everything), which failed.  I then reinstalled OSX with refit and then Ubuntu, but the same thing happened.  If I boot with the 'text' command line option, it gets stuck right after it talks about a usb device.

Any help on how to fix this is appreciated.

Thanks.

---

### Post by yugnip on 2012-01-02
Did you install Grub on the Ubuntu partition? If you install Grub to the root of the HD Ubuntu will not boot.

For example:

/sda - efi
/sda1 -OSX
/sda2 -Ubuntu

You would install Grub to the root of the /sda2 partition and set mount point to /

Do you have more than one linux entry in the rEfit menu?

---

### Post by wiz561 on 2012-01-02
Thank you very much for the response and help.

When I see the refit menu, there's three options:

- Boot EFI\ubuntu\grubx64.efi
- Bot Mac OS X from Macintosh HD
- Boot Legacy OS from HD

When I choose the grubx64.efi, Grub pops up with a number of choices...

- Ubuntu
- Recovery
- memtest
- OS X 32 bit on /dev/sda2
- OSX 64 bit on /dev/sda2

The MBR partition layout goes....

sda1 - EFI Protective
sda2 - OSX HFS
sda3 - Linux (root /)
sda4 - swap

The boot loader is on sda3.

Ubuntu does kind of boot.  In the 'recovery console' boot, it gets to the point "Recovery Menu", and then things lock up.  Not exactly sure why....

Thanks again in advanced for any help.

---

### Post by yugnip on 2012-01-02
Hmm, are you certain Grub is on the partition and not the root? The three entries in rEfit would seem to indicate otherwise.

To get rid of the third entry, in mac terminal run:

```
sudo fdisk -u /dev/disk0
```

If that doesn't allow you to boot normally into Ubuntu, then try formating the partition and reinstalling. Please note that in the installer you should choose 'do something else' to correctly format, set mount point and install the bootloader (Grub) to /sda3. The bootloader is the dropdown menu, and is set automagically to install at / , which you don't want. Scroll through the list until you see /sda3 and install there.

All this assuming you have made a backup of your important mac files first :p

Hope this helps.

---

### Post by wiz561 on 2012-01-02
Thanks for the responses.  I don't care about the mac partition.  It can be trashed, since nothing of importance is on it.

I did not do the fdisk command yet.  I don't think it's a partition problem, but I could be wrong.  When I plugged a USB keyboard in, it allowed me to boot up into recovery mode without any problems.  The non-recovery mode still doesn't consistently boot all the time.  

I think it's a hardware or device problem because it does get past grub, it just fails on the ubuntu load.  Nonetheless, I'll try the fdisk thing and report my results...

thanks!

---

### Post by wiz561 on 2012-01-02
I tried to do the fdisk -u /dev/disk0 to update the MBR within OSX.  Rebooted, and the same thing is still going on.  :(

Thanks, still open for ideas though!

---

### Post by wiz561 on 2012-01-03
Strange.  I downloaded the...

ubuntu-11.10-desktop-amd64+mac.iso 

and used that to install, instead of the amd64 alternate disc.  Everything works fine.

It's frustrating because it would be good to know why the +mac version works but the others don't.  In the end, I'm glad to know that it works though.  :)

---

### Post by yugnip on 2012-01-03
Glad to hear you got it running.  Everything working well so far?

---

### Post by wiz561 on 2012-01-04
Yes, so far so good....which makes me happy.

I'm still curious about the differences in the ubuntu 'mac' version.

Thanks!

---

### Post by manvvip on 2012-04-20
I also want to know whats special about the "Mac" edition, and why it works so well?

---

