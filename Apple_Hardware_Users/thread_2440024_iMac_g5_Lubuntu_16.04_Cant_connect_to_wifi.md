---
title: "iMac g5 Lubuntu 16.04 Cant connect to wifi"
date: 2020-04-04
forum: Apple Hardware Users
---

### Post by wiicart on 2020-04-04
Ive installed lubuntu 16.04 on my iMac g5 but I cant connect to internet, I have a airport extreme card. Ive tried installing drivers but either i've installed them wrong or they just arent working

---

### Post by jeremy31 on 2020-04-04
Moved to Apple

---

### Post by gsahli on 2020-04-04
I don't have one of those...
If I understand correctly, your A/Extreme card is either Atheros or Broadcom. If it is Broadcom, you should follow the instructions here:
[https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

This command (terminal) may help you figure out which card you have:
sudo lshw -C network

---

### Post by mörgæs on 2020-04-05
Lubuntu 16.04 is out of support. Better to begin with a clean install of 19.10.

---

### Post by guiverc on 2020-04-05
Lubuntu 16.04 LTS being a flavor of Ubuntu had only 3 years of supported life ([https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/) [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)) which ended 2019-April. Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7) have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case.

The powerpc (`ppc`) architecture was supported by main Ubuntu 14.04 LTS, and by some flavors for 16.04, however both are now EOL (*end-of-life*) and only `ppc64el` is still supported for power pc, however ppc64el won't run on mac hardware (mac switched to intel instead and never produced 64 bit powerpc devices)

---

### Post by mörgæs on 2020-04-05
Sorry, I forgot about the PowerPC problem.
Please ignore my post.

---

### Post by wiicart on 2020-04-05
I tried the wiki.ubuntu.com solution but that didn't work, I looked at this [https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro](https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro) and on the first answer it said to do[COLOR=#242729][FONT=Consolas]sudo mkdir /lib/firmware/b43[/FONT][/COLOR]sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -rv b43 
sudo modprobe -v b43
This did get wireless working but it stops working after restarts and you have to run those commands again

---

### Post by gsahli on 2020-04-05
Good progress. Some background: the Broadcom chipset requires that the firmware part of the driver be re-installed onto the chip at each restart. The permanent module is supposed to do this.
Review this for permanently loading modules
[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

PS: I haven't had to do this since around 2005 - so I'm just giving hints!

---

### Post by wiicart on 2020-04-06
> **gsahli said:**
> Good progress. Some background: the Broadcom chipset requires that the firmware part of the driver be re-installed onto the chip at each restart. The permanent module is supposed to do this.
Review this for permanently loading modules
[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

PS: I haven't had to do this since around 2005 - so I'm just giving hints!

This helped a lot! Thank you

---

### Post by ernsteiswuerfel on 2020-06-21
[INDENT]If you want a much more painfree experience with Linux on G3/G4/G5 hardware just skip this outdated distro and use another one. Also G3/G4/G5 PPC is no longer supported by Ubuntu.

These are (better) alternatives with bootable isos, current software (working browser, etc.) and current kernels:
[https://voidlinux-ppc.org/](https://voidlinux-ppc.org/)
[https://www.adelielinux.org/](https://www.adelielinux.org/)
[https://fienixppc.blogspot.com/p/download.html](https://fienixppc.blogspot.com/p/download.html) (64bit only, USB boot image)

Also no need to fiddle around with yaboot any longer. Void and Adelie use grub just like you know it from Linux on regular x64_64 hardware.[/INDENT]

---

