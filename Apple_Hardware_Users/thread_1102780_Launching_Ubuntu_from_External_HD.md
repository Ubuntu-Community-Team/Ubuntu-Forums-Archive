---
title: "Launching Ubuntu from External HD"
date: 2009-03-22
forum: Apple Hardware Users
---

### Post by Ryupower on 2009-03-22
Hi all!

I have a macbookpro, I think it's version 4.1.
Anyways, on my windows desktop computer I installed ubuntu on an external hard drive. When the hard drive is attached, the GRUB menu will start, when not, it'll just load XP. Just how it's supposed to work.

So I tried attaching the external hard drive to my macbook pro, and tried booting it with refit. Yes, it shows a penguin icon in the refit boot menu, however, when I attempt to boot it, all I get is a black screen with one word on it:
GRUB

And it stays there. Nothing happens. I need to push the power off button to shut the thing down again.

To some of you this might seem like a stupid novice question, but any help appreciated. Thank you!

-r

---

### Post by pxwpxw on 2009-03-22
> **Ryupower said:**
> Hi all!

I have a macbookpro, I think it's version 4.1.
Anyways, on my windows desktop computer I installed ubuntu on an external hard drive. When the hard drive is attached, the GRUB menu will start, when not, it'll just load XP. Just how it's supposed to work.

So I tried attaching the external hard drive to my macbook pro, and tried booting it with refit. Yes, it shows a penguin icon in the refit boot menu, however, when I attempt to boot it, all I get is a black screen with one word on it:
GRUB

And it stays there. Nothing happens. I need to push the power off button to shut the thing down again.

To some of you this might seem like a stupid novice question, but any help appreciated. Thank you!

-r

To boot external with an intel mac mbp41 you need EFI bootloader grub.efi on the external, and to do that -

a small fat322 or a hfsplus partition on the external, to put files grub.efi, grub.cfg,  grub.icns.

a kernel version 2.6.26 or later.

depending on the age of the MBP you may need grub32.efi or grub64.efi - "About rEFIt"  will tell you.

and rEFIt on OSX to run grub.efi.

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by Ryupower on 2009-03-23
Thank you, I didn't know there was a 'GRUB' for OSX using refit. Thanks, I'll try this ASAP

---

