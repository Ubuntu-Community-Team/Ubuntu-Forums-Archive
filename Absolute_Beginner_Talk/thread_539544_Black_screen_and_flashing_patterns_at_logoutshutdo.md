---
title: "Black screen and flashing patterns at logout/shutdown"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-08-31
Hi! Lately the screen has started black out when I log out or shut down the computer (also when ctrl+alt+backspace). I found some issues like this, but in my case there also appears a flashing pattern on the screen. Then I have to force my computer to shut down. Also, in the other issues it usually depends on an nVidia driver. But I've got Intel chipset (FSC Amilo laptop). I'm running 7.04. The problem hasn't always been there, it appeared not long ago, so I assume it has something to do with an update or something. And it doesn't happen everytime I shut down, but quite often.

Thanks
Joakim

---

### Post by dstew on 2007-08-31
This is probably an issue with the "splash screen" that hides the system messages when booting or shutting down. A simple thing to try is booting the kernel using the "nosplash" option. You can try this once by editing the kernel line when you first see the grub menu choices. Hit 'e' to edit, use the up and down arrows to select the kernel line, hit 'e' again to edit this line, and change **splash** to **nosplash**. Then, hit return to save the edit, and 'b' to boot. You should see the system messages now at startup.

When you shutdown, you should also see some system messages, but hopefully it will shutdown more cleanly. If this helps your system, you can make **nosplash** permanent by editing the  kernel line in the /boot/grub/menu.lst file.

EDIT: If you want to see all the boot and shutdown messages, remove **quiet** from the kernel line.

---

### Post by Joakim Stokland on 2007-08-31
Thanks, I'll try that! :) I'll let you know whether it works or not.
Joakim

---

