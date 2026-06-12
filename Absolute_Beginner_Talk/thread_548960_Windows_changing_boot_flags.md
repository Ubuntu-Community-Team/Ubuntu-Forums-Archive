---
title: "Windows changing boot flags"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by crav on 2007-09-11
For various reasons, I HAVE to have a Windows partition. I followed the guide from my sig and installed TinyXP. I did all the steps involving grub, everything worked.
I was able to boot into Ubuntu no problems. I rebooted and started up Windows, again, no problem. When I rebooted once again to make sure everything was working out, the Windows MBR had taken over. I threw in the GParted LiveCD to check if something had changed, and it seems that TinyXP changed the bootflags and made the Windows partition bootable, but not the Ubuntu partition. I switched the flags, and rebooted one more time, to see if it would happen again. It did.

Any one know a way to keep Windows from resetting the bootflags, that way I boot to GRUB?

---

### Post by Shazaam on 2007-09-11
Is grub installed to the MBR? You might be able to change the default OS. Boot your Ubuntu live cd and edit grub.
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

### Post by crav on 2007-09-12
Thanks, but that doesn't really answer my question. Is there anyway to maybe overwrite the windows bootloader or prevent windows from altering the bootflags?

---

