---
title: "Grub error 15 with /home on seperate hard drive."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by a.swan89 on 2008-02-06
So I decided to reinstall Kubuntu 7.10 with /home on a new hard drive I got for black friday. It was working wonderfully until I did something stupid and borked my installation. I decided that since all my stuff was on the separate hard drive I would just reinstall Kubuntu. I went through the installation process, manually editing the partitioner so that /home was mapped to the same drive that I was using for /home before, hoping that I would be able to keep all my old stuff. Now when I boot I get a GRUB error 15. I took a look at /etc/fstab and I can't see anything wrong.

proc           /proc     proc    defaults                                   0     0

/dev/sdb2   /           ext3    defaults, errors=remount-ro    0     1

/dev/sda1   /home   ext3    defaults                                   0    2

/dev/sdb1  none     swap  sw                                           0   0

and then my cd and floppy drive configs. Any suggestions?

---

### Post by phidia on 2008-02-06
This gentoo [guide]("http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable") is, I think, the clearest-although not all the situations there will apply-reading that can provide you with a fix. 
Has your bios setting changed since the 1st install?

---

### Post by jw5801 on 2008-02-06
/etc/fstab won't affect grub in the slightest. Mounting your home partition doesn't come until long after grub. It has to be handled by the kernel which can't be mounted until after grub runs succesfully.

There's some info about grub error 15 [here](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable). You might want to use the LiveCD to boot into your system, check that everything works alright and have a look in the /boot/ directory to see what's there. You might also want to check /boot/grub/menu.lst. If that looks ok you can try running ```
sudo grub
find /boot/grub/stage1
root (hdX,Y) # where X and Y are as returned by "find"
setup (hdX) # as returned by "find"
```
To setup grub again!

---

