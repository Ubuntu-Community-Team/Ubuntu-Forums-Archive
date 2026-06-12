---
title: "Open Firmware Password Reset?"
date: 2008-01-07
forum: Apple Intel Users
---

### Post by pjd109 on 2008-01-07
Hi guys, I recently wanted to try Ubuntu Linux on my Mac Mini. I figured I would install it, play around a little, and go back to OS X. Turns out, I forgot to disable the Open Firmware password, and I've ended up forgetting it. Is there a way for me to reset it, like booting the disc in Linux? I tried the startup shortcuts to zap the PRAM and to get to Open Firmware but they don't work. I know this has probably been posted a few times, but I couldn't find any sort of concrete answers one way or the other. Thanks for any help

---

### Post by cyberdork33 on 2008-01-07
> **pjd109 said:**
> Hi guys, I recently wanted to try Ubuntu Linux on my Mac Mini. I figured I would install it, play around a little, and go back to OS X. Turns out, I forgot to disable the Open Firmware password, and I've ended up forgetting it. Is there a way for me to reset it, like booting the disc in Linux? I tried the startup shortcuts to zap the PRAM and to get to Open Firmware but they don't work. I know this has probably been posted a few times, but I couldn't find any sort of concrete answers one way or the other. Thanks for any help
This is the _Intel_ Apple forum which does not use Open Firmware, (rather uses a closed EFI implementation). You might try in the [PPC forum]("http://ubuntuforums.org/forumdisplay.php?f=133").

---

### Post by pjd109 on 2008-01-07
In Leopard, they refer to the firmware password as an Open Firmware password. This is on an Intel-based Mac Mini. If it's still in the wrong place, I apologize. Maybe someone could help me in regards to booting the DVD through GRUB?

---

### Post by cyberdork33 on 2008-01-07
> **pjd109 said:**
> In Leopard, they refer to the firmware password as an Open Firmware password. This is on an Intel-based Mac Mini. If it's still in the wrong place, I apologize. Maybe someone could help me in regards to booting the DVD through GRUB?
Open Firmware was used in PPC Macs, not Intel Macs. I really don't understand what the issue is if you have an Intel Mac.

I don't know what you mean by booting a DVD through grub... you just hold c at bootup to boot from the optical drive.

---

### Post by pjd109 on 2008-01-07
The password prevents the user from booting via the disc drive (holding c). Until I find another way, I'm stuck within Ubuntu. I had just assumed that I could find another way.

---

### Post by cyberdork33 on 2008-01-07
> **pjd109 said:**
> The password prevents the user from booting via the disc drive (holding c). Until I find another way, I'm stuck within Ubuntu. I had just assumed that I could find another way.It looks as though setting a firmware password blocks you from resetting the PRAM and many other functions, and it also looks like you need to boot OSX in order to remove/change the password.

This article does mention that it can be done by opening the computer...
[http://docs.info.apple.com/article.html?artnum=106482](http://docs.info.apple.com/article.html?artnum=106482)

The only other method I could think of would be to swap the hard drive for one that had OSX installed...

You can get grub to boot OSX... whether that means you can get it to boot from a DVD or not, i do not know, but this may help: [http://forum.insanelymac.com/lofiversion/index.php/t3622.html](http://forum.insanelymac.com/lofiversion/index.php/t3622.html)

More info that may be helpful:
[http://forums.macosxhints.com/showthread.php?t=59357](http://forums.macosxhints.com/showthread.php?t=59357)
[http://macosx.com/forums/mac-os-x-system-mac-software/270395-forgot-firmware-password-macbook-pro.html](http://macosx.com/forums/mac-os-x-system-mac-software/270395-forgot-firmware-password-macbook-pro.html)

---

