---
title: "Ubuntu wont show up in the OS X boot loader"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by k06eg02 on 2008-05-11
To start: I have a MacBook 2.0 GHz Core 2 Duo from late 2006 with 2 GB of RAM and an 80 GB hard drive running OS X Leopard (10.5.2).

I followed the MacBook wiki for installing Ubuntu 8.04 onto the "Windows" partition of my hard drive that I created with boot camp. As I understand it, I don't need rEFIt in order to make this work and I would prefer to just hold down alt/option when I want to go into Ubuntu. However, I have installed Ubuntu according to the wiki, and the partition doesn't show up in the boot loader when I hold down alt/option at the boot - all that shows up is the Macintosh HD.

I'm quite new to this, so it is possible that I've messed something up. When in the Ubuntu installer, I deleted the /dev/sda3 volume and replaced it with the ext3 volume mounted at / for Ubuntu to use. I wasn't sure about where I need the boot loader in the advanced options of the install, so I didn't change it from (hd0).

If anyone has an idea why it isn't showing in the boot loader when I hold down alt/option it would be a big help. Also, if anyone has a better guide to installing Ubuntu using boot camp without rEFIt I would appreciate that as well.

Thanks for you help. It's greatly appreciated

---

### Post by SeeLos on 2008-05-11
I seem to have the exact same problem as you. I've tried a few variations as well (swap space and no swap space, guided and manual partitioning, and installing boot loader to the 3rd partition (ubuntu one)). I too would like to avoid using refit, but am wondering if it is necessary now because of something new 8.04 does with the mbr as I've installed feisty fawn and gutsy gibbon before with no problems and without refit. Thanks..

---

### Post by k06eg02 on 2008-05-11
I'm wondering if we install gutsy gibbon using the method that we know works and then update it to hardy heron if the boot loading issue will be resolved. I'm in the process of downloading 7.10 to see if it works that way. Thanks.

---

### Post by SeeLos on 2008-05-11
K06eg02, I finally gave up and gave the refit method a shot and it worked. I then uninstalled it and my system works just how I hoped it to. So if you have already ran the installer and want to boot, just boot os x, install refit, reboot, click partition tool, click 'y' to update or sync ur mbr, i rebooted for good measure. at this point you should be able to continue to use refit for when you boot to get the option of what you would like to boot (ubuntu finally worked) or what i did was booted os x again and uninstalled refit and now use the option key when booting to select my ubuntu partition. hope this helps for now, i'm pretty new at this as well though so sorry for the lack of technical explanations, but this should get you by for now!

---

### Post by k06eg02 on 2008-05-11
SeeLos-

Just a quick question: Did you end up using a swap partition as well as a partition for Ubuntu, or did you just use the one partition?

Thanks for you help by the way.

---

### Post by SeeLos on 2008-05-11
I did end up using a swap partition, goodluck.

---

### Post by cyberdork33 on 2008-05-11
yes there is a bug in the hardy installer so you have to sync the partition tables before things will work properly. This can be done in refit and then after uninstalling it, you should be able to do as you want.

---

