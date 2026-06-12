---
title: "What Am I Doing Wrong?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by thebreezer on 2007-04-24
Well downloaded Feisty 7.04, booted to the desktop and clicked install (I did a clean install). Went through the partionning, username etc. The install started...went to bed. The next morning I see the desktop again with the install icon, you know the same screen I had when first booting. No sign of, I don't know, installation complete or reboot your computer. So I restart the computer hoping to get the bootloader (choice of booting into Ubuntu or Windows) Nothing! It just boots into XP. What happened, where did my installation go. Please advise me.


Bruno

---

### Post by Tomosaur on 2007-04-24
Hi,
it sounds as though the installation crashed or something. You have a few options:

1) Download a portable bootloader, such as GAG. This will allow you to try and boot into Linux, even though Grub (the bootloader you SHOULD have) is not installed.

2) Try re-installing. Bit of a pain, but these things can happen sometimes, if there appears to be no damage done, you may aswell just reinstall.

3) Boot the LiveCD, open up a terminal, and type:
```

fdisk -l

```
If you see entries for Linux and for Swap in the output, then chances are it's only the bootloader which failed to install. You could try mounting the Linux partition and checking whether it's all set-up correctly. If you get errors when you try to mount, then it's possible that the partitioning was successful, but there was some problem actually installing the system. If, however, everything appears ok, you can try just installing grub yourself. There are a few guides on this forum on how to manually install the bootloader from the LiveCD.

---

### Post by speeves on 2007-04-24
Can you tell us more about your installation procedure?  Did you try to dual-boot?

thanks,

---

### Post by thebreezer on 2007-04-28
Thanks, but I opted for Xandros instead.

---

