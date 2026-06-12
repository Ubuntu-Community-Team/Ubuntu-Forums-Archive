---
title: "Cant pass the &quot;grub rescue&gt;&quot; screen after installing grub-pc"
date: 2013-10-07
forum: Apple Hardware Users
---

### Post by gandalfuy on 2013-10-07
I'm on a macbook air 3,2. I have been using ubuntu 12.04 with no problems since just the other day:

I was trying to install Nvidia drives, Have been trying that for a while. I always got to a black screen after boot and have to erase nvidia drivers booting from a pendrive (i got used toNouveau, really badly and unstable)

I saw that a new oportunity to run nvidia drivers installing grup pc. 

[http://askubuntu.com/questions/22859...acbook-air-3-2](http://askubuntu.com/questions/22859...acbook-air-3-2)

I read  about Nvidia drivers needing a fake bios, and that grub pc was needed (i think i acted to fast there... :P). Well i installed grub pc and checked the two check boxes after intsllation (i choose wongly the drive to install grub i supouse)

I get to the boot rescue> screen and type this messaje with no success:

grub rescue> set prefix=(hd0,2)/boot/grub
grub rescue> set root=hd0,2
grub rescue> insmod linux
error: invalid arch independent ELF magic.

I ran the the boot repair tool and got this:
[http://paste.ubuntu.com/6207524/](http://paste.ubuntu.com/6207524/)

What should i do?

thanks,
aLe.-

---

### Post by gandalfuy on 2013-10-09
Any suggestion?

---

### Post by oldfred on 2013-10-10
Moved to Apple sub forum.

---

