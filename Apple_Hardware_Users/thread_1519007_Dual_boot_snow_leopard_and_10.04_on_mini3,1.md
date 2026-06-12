---
title: "Dual boot snow leopard and 10.04 on mini3,1"
date: 2010-06-27
forum: Apple Hardware Users
---

### Post by astrashe on 2010-06-27
I'm a new mactel user.  I can get ubuntu to work fine on its own (except for sound, a problem for another day), but I can't get dual booting to work.

I'm using this page as a guide:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I started out with a clean OSX snow leopard install.  I ran bootcamp and shrank my 320G hfs+ file system to 160G.  I installed rEFIt, and rebooted twice (you don't see the menu after rebooting once).  

Then I booted from my 10.04 CD, and deleted the partition created by bootcamp using gparted.

When I run the installer and tell it to use the largest continuous space, it makes the / file system in partition #5, and the swap partition in partition #5.

I figured that might cause problems with a MBR partition table, so I partitioned manually, and set up / in sda3 and swap in sda4.

When I tried to configure the installation of the bootloader, I had a menu of possible places to install it.  The choices were:

/dev/sda
/dev/sda-1
/dev/sda1
/dev/sda2
/dev/sda-1  (listed a 2nd time)
/dev/sda3
/dev/sda-1  (listed a 3rd time)

I picked /dev/sda3, but then the OK button was grayed out.

I'm sure I'm doing something dumb.  Can anyone tell me what it is?

Thanks...

---

### Post by SecretLegend on 2010-06-27
Hey Man I don't know exactly what you are doing wrong but I think you should follow this tutorial:

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required) 

Just follow the steps for Ubuntu not windows and you should be fine. BTW this is how I set mine up :) Hope This Helps

---

### Post by LtPitt on 2010-06-28
Great stuff!

Do you think it's possible to triple boot

Mac os 9.2.2

Mac os 10.3.9

and

Ubuntu 10.4?

I have a rev b imac with 80 gb disk and 512 mb ram (incoming) and I just feel crazy about experimenting :)

---

### Post by linuxopjemac on 2010-06-28
LtPitt: Go for Debian Lenny with LXDE.

---

