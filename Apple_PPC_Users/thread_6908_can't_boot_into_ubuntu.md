---
title: "can't boot into ubuntu"
date: 2004-12-02
forum: Apple PPC Users
---

### Post by dspivey on 2004-12-02
i have two drives, one with os x and classic (os 9), and the other with ubuntu installed.  dual-booting hasn't been a problem at all, that is, until i booted my G4 with os 9.  now when i restart the G4, i don't get the yaboot prompt any more; it just boots into os x or 9.  any ideas on how to get back yaboot?  and if so, is there any way to add os 9 as a startup option in yaboot?  

thanks in advance for any advice

---

### Post by trash on 2004-12-02
try to reboot holding the 'option' key... this should give you all available boot options.

thats as far as I can help, though there are a few yaboot posts around that might belp:)

---

### Post by iant on 2004-12-03
i think this has something to do with apples software automatically replacing the standard apple bootloader when you reboot to OS9 from 'system preferences' in OSX.  try the following: 

follow the quoted instructions below to reboot into ubuntu.  

once in umbuntu, run yabootconfig - this will replace your yaboot bootloader

add the OS9 partition to the yaboot.conf.  (see [http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/))

!!IMPORTANT!!
instead of using the reboot in OSX preferences, from now on just restart the computer and access OS9 from yaboot.


the following came from here.  [http://wijnand.rietman.biz/linux/mac/index.html?main](http://wijnand.rietman.biz/linux/mac/index.html?main)
> 
Open Firmware is the software that controls your "New World" Mac from the time it is turned on until the operating system takes control. You can get into Open Firmware by keeping the buttons "Apple", "ALT", "O" and "F" pressed during system start-up. When in open firmware you can boot yaboot with the following command:

boot hd:9,yaboot

In order to make yaboot the default boot loader, you can change the default boot setting to yaboot with the following command:

setenv boot-device hd:9,\\yaboot
boot

The number 9 needs to be replaced for the partition number where your yaboot resides. In case things went very wrong, you can reset Open Firmware by keeping the buttons "Apple", "ALT", "P" and "R" pressed during system start-up.
 

obviously hd:9 should be replaced with the correct on for the yaboot bootloader.

---

### Post by dspivey on 2004-12-03
thanks very much for your help!  i'll try this over the weekend and let you know my results!

---

