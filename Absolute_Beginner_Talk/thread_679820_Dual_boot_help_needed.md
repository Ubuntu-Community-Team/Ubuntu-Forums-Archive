---
title: "Dual boot help needed"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Liam-Gorham on 2008-01-27
anyone got any idea's on how to do a dual boot with a ubuntu 7.10 80GB HD and a windows 
80GB HD?

---

### Post by torgrot on 2008-01-27
Do you have two hard drives each 80 GB?  What kind of drives are they, SATA or IDE?

torgrot

---

### Post by Liam-Gorham on 2008-01-27
They are both 80gb and Both are sata

---

### Post by mister_pink on 2008-01-27
What set up do you have at the moment? If youre starting from scratch it should be reasonably easy, or if you have win XP first its easy.

Edit: By setup, I mean in terms of installed OS and whether youre bothered about keeping them. See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by torgrot on 2008-01-27
So as I understand you have one drive with windows and a blank drive that you want to install ubuntu on?

torgrot

---

### Post by bumanie on 2008-01-27
Windows prefers to be on the first partition of the master drive. Therefore it best to install it first and ubuntu second. This way grub will see windows and on boot up give you the choicce of which OS to boot.

---

### Post by torgrot on 2008-01-27
This is just the way I installed it.  I had Windows XP on one 160GB hard drive and nothing on the second 160GB hard drive.  I absolutely did not want anything touching the Windows installation.  I disconnected the Windows drive, made the new drive the primary drive, I would boot from.  I installed Ubuntu to it with no difficulties.  I reconnected the windows drive and left it out of the boot sequence.  I then booted into Ubuntu and then updated Grub to allow booting Windows off the second drive.  This way, if something goes terribly wrong in Ubuntu, and it has, I was able to simply change the boot order and boot windows, which I must have for work.

torgrot

---

