---
title: "I want to boot Ubuntu on a USB thumbdrive..because spreadsheet takes 1m:16s to open."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Scolecite on 2007-02-28
I have a Dell CPx  650 PIII with one USB 1.1 port. Im running the edgy version or the one for systems under 192mb of ram (I have 160), and posting this message from it right now. Its working great, its just there is tremendous HD chatter. Opera takes 20 seconds to load up, as does Firefox, and my HD is firing away like a Heavy Machine gun. Im gonna time opening up openoffice spreadsheet program right now! One sec...  

1:16 first time
:50 sec the second time(always loads faster 2nd time, but dosent get really any faster 3rd and so on time)

I want to put Ubuntu on my 4GB flash drive. Problem is that even though Ive updated the BIOS on my notebook there is no selection for USB booting. 

1stly most important question is there hope if UBS boot is not in the BIOS? 
2ndly, should apps be taking as long to start? 
3rdly, Thanks!

---

### Post by arochester on 2007-02-28
See "LiveUsbPendrivePersistent" at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29)

---

### Post by arochester on 2007-02-28
When a computer doesn't have the BIOS capability to boot from a CD you can create a bootdisk on a floppy. The computer will start to boot on the floppy and than pass to the CD-Rom.

Can e.g. SmartBootManager be put on a floppy and recognise/pass to the USB stick? See SmartBootManagerHowto at [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto) . Although ot does say "SBM also does not appear to recognize external USB CD-ROM drives..."

---

### Post by arochester on 2007-02-28
Also see pendrivelinux.com particularly "Booting Linux using USB-ZIP on older systems" and howto install Ubuntu from Windows and Linux

---

### Post by C.S.Cameron on 2007-06-08
Scolecite:
I've installed Ubuntu on a Kingston 4G Traveler.
Works great on every box in the house, except my wifes old celeron,
(If you are willing to settle for default graphics drivers.
Wondering how to multi boot depending on graphics card).
The USB needs to be plugged in when you start bios.
Think I will try arochester's advice to try to get it working on my wife's machine.
Cork

---

### Post by C.S.Cameron on 2007-06-08
Scolecite:
I've installed Ubuntu on a Kingston 4G Traveler.
Works great on every box in the house, except my wifes old celeron,
(If you are willing to settle for default graphics drivers.
Wondering how to multi boot depending on graphics card).
The USB needs to be plugged in when you start bios.
Think I will try arochester's advice to try to get it working on my wife's machine.
If that don't work, i might just install Unbuntu on her hard drive. It gotta be faster and suit her better than windows.
Cork

---

