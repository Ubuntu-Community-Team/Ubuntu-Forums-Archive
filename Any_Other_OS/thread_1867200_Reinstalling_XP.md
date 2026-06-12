---
title: "Reinstalling XP"
date: 2011-10-22
forum: Any Other OS
---

### Post by AlanR8 on 2011-10-22
I've sold my Compaq Mini but the taker wants XP not Ubuntu and no, I didn't make the rescue discs!

I have a genuine XP disc so using my external CD drive I started the installation. Got as far as the first choices screen and got the message that I don't have a hard drive in my computer!

I reloaded Ubuntu from a live CD, used Disc Utility and formatted the HD as NTFS. Tried again and same message.

Any suggestions?

---

### Post by collisionystm on 2011-10-22
> **AlanR8 said:**
> I've sold my Compaq Mini but the taker wants XP not Ubuntu and no, I didn't make the rescue discs!

I have a genuine XP disc so using my external CD drive I started the installation. Got as far as the first choices screen and got the message that I don't have a hard drive in my computer!

I reloaded Ubuntu from a live CD, used Disc Utility and formatted the HD as NTFS. Tried again and same message.

Any suggestions?


Yeah. I assume that you don't have a floppy drive on your computer so you are going to need to download the sata driver for you computer from Compaq.

Use nLite to slipstream the driver into Windows XP and burn a new copy. This new copy will carry the proper driver to install Windows successfully. 

[http://www.nliteos.com/](http://www.nliteos.com/)

---

### Post by nothingspecial on 2011-10-22
Moved to Other Distro/OS Talk

---

### Post by collisionystm on 2011-10-22
If you cannot find a driver on the site, check your bios settings.

---

### Post by SirDrexl on 2011-10-22
It might be that the BIOS has the SATA controller set to AHCI.  Set it  to IDE mode and it should install.  You can leave it that way or install  the AHCI driver after the installation finishes.

AHCI doesn't seem to be a big deal for average mechanical drives anyway;  it improves performance a little, but in real world usage you probably  wouldn't notice the difference.  It's more beneficial for SSDs and  situations where hotswapping is needed.

I would also suggest letting the Windows setup format the drive, instead of formatting ahead of time.

---

### Post by AlanR8 on 2011-10-22
Thanks quys...will let you know.

---

