---
title: "Mint 12 on usb-stick resets everything after a restart."
date: 2013-07-10
forum: Any Other OS
---

### Post by Psmythe on 2013-07-10
I have a similar problem [as in [http://ubuntuforums.org/showthread.php?t=2161351]](http://ubuntuforums.org/showthread.php?t=2161351]). I have Mint 12 on an SD card (4 GB) I use to boot an Eee PC 1001 that has WinXP on the hard drive. I used unetbootin to set up the card. Seems to work fine except for saving most changes. The time zone reverts to London (aka Zulu time) on reboot, Wi-Fi won't connect without re-entering the password, and the user guide I downloaded (to the card) disappeared on reboot, too. The actual time is correct (for the time zone), so that is getting picked up from the BIOS clock OK. I tried to add Skype using the Program Manager, but it said I didn't have enough room on the card, yet I was able to install Skype using APT, and it is saved on the card and works fine. 

I have been reading the "Please help - Kubuntu reverts to Zulu time, will not let me correct this" thread but haven't had a chance to try any of the suggestions yet. I thought the problem might have been my SD card, but I see you have the same problem with a USB stick and gotnexusbluz is using an HD partition, so maybe it is something else.

---

### Post by oldos2er on 2013-07-10
Moved to Other OS/Distro Support.

---

### Post by sudodus on 2013-07-10
> **Psmythe said:**
> I have a similar problem. I have Mint 12 on an SD card (4 GB) I use to boot an Eee PC 1001 that has WinXP on the hard drive. I used unetbootin to set up the card. Seems to work fine except for saving most changes. The time zone reverts to London (aka Zulu time) on reboot, Wi-Fi won't connect without re-entering the password, and the user guide I downloaded (to the card) disappeared on reboot, too. The actual time is correct (for the time zone), so that is getting picked up from the BIOS clock OK. I tried to add Skype using the Program Manager, but it said I didn't have enough room on the card, yet I was able to install Skype using APT, and it is saved on the card and works fine. 

I have been reading the "Please help - Kubuntu reverts to Zulu time, will not let me correct this" thread but haven't had a chance to try any of the suggestions yet. I thought the problem might have been my SD card, but I see you have the same problem with a USB stick and gotnexusbluz is using an HD partition, so maybe it is something else.

Have you got a persistent live system (with a casper-rw file)? In that case all changes except updates of the kernel ***should work***, but very slowly and prone to breakage. There is a risk that you remove the card/pendrive before all content is written from RAM to the slow flash memory. I think the time setting in live sessions suffers from a bug, at least in the developing version, Saucy (to become 13.10).
 
If things are saved sometimes and sometimes not saved, it could be because sometimes you boot with the boot option persistent, and sometimes not.

---

### Post by drawkcab on 2013-07-10
If you set up your live usb with unetbootin, then no.

Best way around this is to set it up within ubuntu using their live usb creation tool which automatically sets up a persistence file.  

The other option is to install ubuntu to a usb or sd card and then boot from it when necessary.

---

### Post by cpatrick08 on 2013-07-10
you an use a persistence on unetbootin it is near the bottom and says it is for ubuntu distros only.

---

