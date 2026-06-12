---
title: "Grub2 no boot after changing IDE to AHCI on Bios!"
date: 2019-12-20
forum: Any Other OS
---

### Post by marcelosofth on 2019-12-20
Hello friends, I am using Grub2 and after changing in Bios from IDE to AHCI the boot does not work anymore, does anyone know anything about this problem?

Ps. If I went back to Bios again for IDE the boot with Grub2 works normally!

In the image below is the contents of my grub2.cfg file, I believe where blue is the problem! "insmod ahci" ? ](*,)

[https://cdn.discordapp.com/attachments/562716448401784833/657406481020223489/unknown.png](https://cdn.discordapp.com/attachments/562716448401784833/657406481020223489/unknown.png)

---

### Post by oldfred on 2019-12-20
Moved to other OS since not Ubuntu.

What version of grub?

       2.04 Out of memory error loop mount
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)
Links in FAT32 error:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534)

---

