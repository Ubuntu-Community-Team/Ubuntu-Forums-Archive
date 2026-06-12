---
title: "Grub editing and Dapper Drake"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Metta on 2006-04-22
Hi

I have had to reinstall ubuntu 5.10 several times in the last two days. (Messed up, and no where to go)!. 

Before then, I installed an old version 5.04 until a friend gave me 5.10. So now I have on grub:
5.10, 5.04 and XP on the boot sequence. 

I did try editing grub using: sude gedit/boot/grub/.lst, but with no luck. Can somebody help me with the right editing text. 

Also I recieved an email this morning, explaining about Dapper Drake, I followed the upgrading instructions and edited the terminal with:  gksudo "update-manager -d"

All went well and the download manger kicked in, then told me that the install had completed, I then rebooted, but 5.10 was what I got, and not the newer version, any ideas. 

Thanks

---

### Post by mostwanted on 2006-04-22
It's not *sude gedit/boot/grub/.lst*, it's *sudo gedit /boot/grub/menu.lst*

---

### Post by aysiu on 2006-04-22
Gedit works only if you're using Gnome.

If you're in text mode or if you're using KDE or XFCE, Gedit may not work.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` will always work.

To save when you're done, press *control-x, y, Enter.*

---

### Post by Metta on 2006-04-22
Thanks for that, any ideas regarding Dapper?

---

### Post by aysiu on 2006-04-22
[QUOTE=Metta]Thanks for that, any ideas regarding Dapper?[/QUOTE] What exactly were these upgrading instructions?

---

### Post by mostwanted on 2006-04-22
[QUOTE=Metta]Thanks for that, any ideas regarding Dapper?[/QUOTE]

What makes you sure you're running Breezy? What version of Gnome is available (System &#8594; About Gnome)?

---

### Post by Metta on 2006-04-22
Hi

The instructions I got from:

[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

Gnome version is:

2.12.1

build date 03 10 05

Hope this helps.

cheers

---

### Post by aysiu on 2006-04-23
[QUOTE=Metta]
[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)[/QUOTE] That's weird. I'd assume instructions for upgrading on the official Ubuntu website would actually work: > Upgrading from Ubuntu 5.10

A new version of the Update Manager application has entered breezy-updates which can upgrade your entire system in a few simple steps.

To perform the upgrade:

   1.

      Update your system to ensure that you have the latest version of Update Manager and associated packages. The necessary versions are available from the breezy-updates repository, which is enabled by default.
   2.

      Run the following command (either via ALT-F2 or a terminal):

gksudo "update-manager -d"

    *

      The "-d" switch instructs Update Manager to consider pre-release versions, including this Beta release. Without this switch, only official, final releases will be considered.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.  But I've never tried this myself, so I can't vouch for it--and it didn't appear to work for you.

I would use these instructions instead, as... I wrote them, and I used them to upgrade two computers to Dapper: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

