---
title: "No OSX bootup..."
date: 2007-09-23
forum: Apple Intel Users
---

### Post by jamesotron on 2007-09-23
Hi everyone.

I decided the other day that I'd had enough of OSX and I used fdisk to convert my OSX parititon to a Linux LVM partition and migrated and extended my root partition to take up all the space previously occupied by OSX :D

Now when I power the machine on the EFI gives me a grey folder icon with a question mark in it for a second or so before falling back to legacy MBR boot (and booting via Grub into Linux).  I'm wondering if there is a way to tell the EFI to just boot straight into Grub without looking for the (now missing) HFS+ volume?  With PowerPC it would just be setting the boot command line in open firmware.  Oh for the old days :)

---

### Post by pxwpxw on 2007-09-24
**jamesotron**

Good question.

After a re-read of documentation on 
[http://refit.sourceforge.net/info/boot_process.html](http://refit.sourceforge.net/info/boot_process.html)

As I read it, the Apple firmware is by default looking for a "blessed" folder and efi bootloader, usually provided by Macosx, then goes to the compatibility support module (CSM) for MBR loaders. 

Possible efi loaders are elilo and refit, but refit needs Macosx to get set up (therafter a small hfs+ partiton will do) and I cant find an elilo that works.

Is the result with the Option key any different to a straight power up start?

Yes, bring back open firmware.:)

---

### Post by cyberdork33 on 2007-09-24
you probably should have uninstalled refit first... 
[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

---

