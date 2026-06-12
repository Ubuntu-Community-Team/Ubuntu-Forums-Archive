---
title: "Asus p8z77 ws"
date: 2012-05-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by adamrosas on 2012-05-29
Video driver's appear to be broken with this motherboard, black screen
when booting, if I set "nomodeset" then I get video and reach the 
desktop but large black border and 800x600 resolution the 
last text printed to the screen without the "nomodeset" option is
"hw conflict removing EFI_VGA" or something to that effect.
I tested Nvidia and ATI video cards same result.
OS's tested were Xubuntu x64 12.04 and Linux Mint 13.

I contacted ASUS support because the same hardware and software
works on an ASUS P8P67 motherboard, the reply email directed me
to their support FAQ which had nothing regarding this issue.

EDIT:

The exact text of the last line printed to screen is
"fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver"
then the system becomes unresponsive. 
I installed Xubuntu 12.04 an tried the Nvidia driver still no good.

---

### Post by adamrosas on 2012-05-31
I got it working, "nomodeset" to boot install media, "nomodeset"
to boot post install, install Nvidia drivers do not reboot open
command prompt and type "sudo nvidia-xconfig" for some reason 
the Nvidia installer fails to write the config file Xorg.conf
after that all works as expected.

---

