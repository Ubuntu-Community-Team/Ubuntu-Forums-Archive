---
title: "Install ubuntu from external hard disk?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-08-02
I have searched at the forum and didn't find anything helpful.
Topic explains it all; I want to install ubuntu **from** my external usb hard drive to the same hard drive. I do not have any cd's.

---

### Post by the_axiom on 2007-08-02
bump

---

### Post by milosz.galazka on 2007-08-02
You can try something like this:

Install on that drive ubuntu and *ubiquity* package.

Boot from that drive and run *sudo ubiquity*

Probably you will need to tweak system on that drive...

---

### Post by milosz.galazka on 2007-08-02
> **the_axiom said:**
> bump

Hi, could you explain me what does it mean? I am not a native English speaker :)

Yes, I know that this post is somewhat offtopic

---

### Post by jgrabham on 2007-08-02
> **milosz.galazka said:**
> Hi, could you explain me what does it mean? I am not a native English speaker :)

Yes, I know that this post is somewhat offtopic

It means that the post wasn't answered for a long time, so he wanted to get it back up on the first page.

---

### Post by the_axiom on 2007-08-02
stands for **B**ring **U**p **M**y **P**ost

---

### Post by pyros on 2007-08-03
Are you running windows on the internal hard drives? if so, take a look at Wubi:
[http://wubi-installer.org/](http://wubi-installer.org/)
they have their own subforum here as well, under the 3rd party section.

---

### Post by ugm6hr on 2007-08-03
I have never done this - but it should work in theory....

You will need to create partitions on the USB-disk first.  I would normally use Gparted LiveCD - but you don't have CDs....  So, you will need an additional USB-flash-disk.

You could create the partition from a LiveUSB of DSL.  See this: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

Then boot from the DSL LiveUSB, and create 1 primary partition on the USB-disk (at the end of the disk, leaving the rest unpartitioned.  I use the command *cfdisk* (see [http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cfdisk](http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cfdisk)).  Create the partition at the end of the USB-disk, and make it about 1-1.5GB.

Then, follow this: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

Then, you should be able to boot from the USB-disk.  This should allow you to install to the same HD...

Give it a try - and report back if it works.

However - it would be an awful lot easier to just get some CD-Rs :)

---

