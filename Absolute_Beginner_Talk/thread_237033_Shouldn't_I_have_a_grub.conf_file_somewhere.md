---
title: "Shouldn't I have a grub.conf file somewhere?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-15
I have Ubuntu Dapper installed on my hard disk with Grub as the bootloader in the MBR.
However, there is no grub.conf file in my /etc/ directory.

Am I looking in the right place?

---

### Post by steve.horsley on 2006-08-15
There is not one on my PC either. 
Do you mean /boot/grub/menu.lst?

---

### Post by fluffnik on 2006-08-15
> **PaulFXH said:**
> I have Ubuntu Dapper installed on my hard disk with Grub as the bootloader in the MBR.
However, there is no grub.conf file in my /etc/ directory.

Am I looking in the right place?

Grub's configuration is stored in /boot/grub/ rather than /etc/ because it needs to be available very early in the boot process when /etc/ might not yet be.

The file you're most likely to want to tweak is /boot/grub/menu.lst, it's quite well commented and not *too* scary but do back it up before editing!

There is a very useful comand called "locate" - or better "locate -i" which is case insensitive - which will find things very quickly, provided it was there since last indexed.

---

### Post by PaulFXH on 2006-08-15
Thanks for the replies.
Yes, as both of you have said, I'm aware of the /boot/grub/menu.lst file.
However, I'm trying to make a triple boot system as outlined in this link:

```
http://www.linux.com/article.pl?sid=06/03/31/2222259
```

which specifically refers to adding a LILO-compatible Linux distro to a dual-boot system based on Grub.
But, as you can see in the following, he refers to this mysterious /etc/grub.conf file which is perhaps an error.

> This method of using the Fedora GRUB bootloader instead of the Xandros LILO is quite flexible, since one may simply edit the Fedora /etc/grub.conf file to add or delete operating systems

Nevertheless, it is absolutely central to the central point of his article.

I'd welcome any comments on this.

---

### Post by kaens on 2006-08-15
If I remember correctly, grub.conf is what rpm-based distros (or at least Fedora) call menu.1st - in other words, they are the same file.

---

### Post by PaulFXH on 2006-08-15
Yeah, it seems that the /etc/grub.conf file may be some type of evolutionary remnant that has been overtaken by the /boot/grub/menu.lst

---

