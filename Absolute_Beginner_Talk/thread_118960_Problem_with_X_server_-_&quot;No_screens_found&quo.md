---
title: "Problem with X server - &quot;No screens found&quot;"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Lege on 2006-01-18
Hello,

I've just installed Ubuntu Linux, and I'm running into the problem "Screens not found" reported by X server when it tries to run.

What happens is when Ubuntu is finished loading the screen flashes black three times when X server starts running, then gives me an error log and kicks me back into the console. I'm suspecting this is done by a virus, since I specifically installed Ubuntu on my box to see what's going on with Windows. When I'm booting up with Windows XP, the Windows loading screen is displayed briefly, and after loading the screen flashes black a few times and reboots automatically.

The X server error log says that it has found correct drivers for my video card, so the problem can't be about video card drivers missing. The network settings are working fine as well, since Ubuntu was able to automatically download the Finnish language pack.

My video card is a few months old ATI Radeon X800 which has worked without any problems before. I installed the 64 bit version of Hoary Hedgehog since I'm using AMD Ahlon Venice 64 3500+.

Do I have to format my Windows and Linux partitions, or is there any other solution? Any help would be appreciated.

---

### Post by The Grum on 2006-01-18
Could you post your xorg.conf file?

---

### Post by Gandalf on 2006-01-18
Can you post the output of /var/log/Xorg.0.log ?? if u donno how just copy it to a floppy disk / usb flash memory and send the content from another computer

EDIT:Like **The Grum** suggested, post also ur /etc/X11/xorg.conf file contents

---

