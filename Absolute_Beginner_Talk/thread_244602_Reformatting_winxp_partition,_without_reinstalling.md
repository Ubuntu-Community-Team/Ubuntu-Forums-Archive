---
title: "Reformatting winxp partition, without reinstalling ubuntu"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-26
Hi,
I have a latop top set up to dual boot.
First I installed windows then I installed ubuntu.

I want to format the winxp partition and re install windows again. Can I do this without having to install ubuntu again.

I assume Id need to fiddle with grub..........

Thanks for any help!

---

### Post by firebird45331 on 2006-08-26
I'm relatively new, but I don't believe you can.  when you start up the windows installation I believe I read somewhere that it will take the whole disk.

---

### Post by Bachstelze on 2006-08-26
No you can't, XP's install will erase your MBR and install it's loader instead. But recovering GRUB after the install is a very simple process. You can alo make your GRUB unbreakable, but then you'll have ton install it on the Ubuntu partition and not the MBR, so either way you'll need to reinstall GRUB - but you will **not** need to reinstall the whole Ubuntu, it will still be there, though wou won't see it until GRUB is reinstalled.

Search the Wiki for GRUB, it will tell you all about it :)

---

### Post by m.musashi on 2006-08-26
I just did this. I reformatted my windows partiton and reinstalled windows. My ubutnu partition is currently not accessible becuase windows reclaimed the MBR. Once GRUB is reinstalled, however, everything is back to normal.

EDIT [This page](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) has good info on doing this. I chose to use the "super grub disk" application. Boot from it and it easily restores GRUB.

---

