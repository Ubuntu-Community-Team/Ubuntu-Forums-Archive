---
title: "Blank Screen During Boot"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-12-25
Hey guys,

Dell Inspiron 6000, loaded 7.10 everything booted alright the first time, I then installed Wine, SwiftWeasel, SwiftDove and Adobe Photoshop.  now when I boot up the screen goes black when it is supposed to be the Ubuntu progress bar, and it stays blank.  When i boot into recovery mode its fine.  Any ideas?

thanks

---

### Post by spiderbatdad on 2007-12-25
your screen resolution might be causing the problem. check /etc/usplash.conf and confirm that xres and yres are compatible with your screen. I had to set mine to 1024 768 for this laptop to solve that problem. ```
gksu gedit /etc/usplash.conf
```

---

### Post by poordamnedfool on 2007-12-25
didnt work, the problem is well before it boots into gui, there is something with the boot splash screen with the progressbar, when it loads in recovery mode its fine.

---

### Post by spiderbatdad on 2007-12-25
yes the problem prevents usplash from starting...did you make the changes and save them?

---

### Post by poordamnedfool on 2007-12-25
ya i changed it to 1280x768 and tried to reboot it didnt do anything... ill try 1280x800 and see if it works.  but how come i can boot into recoverymode just fine?  thanks for the help

---

### Post by spiderbatdad on 2007-12-25
idk but the only other work around i've seen is to add vga=791 to the end of the "kernel" line in /boot/grub/menu.lst   (lst as in list, not 1st.)

---

### Post by poordamnedfool on 2007-12-25
Thanks, this didnt seem to work either, it was working fine until i installed wine and the restricted driver... i think that im just gonna reinstall...  thanks for the help though.

---

### Post by THLopes on 2007-12-26
Hey Guys, this tip worked for me: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

Now I have a splash appearing on boot, and no more slowboot.

---

### Post by poordamnedfool on 2007-12-27
Thanks a lot for the help the guide wrapped up what he was saying and i was able to get it working again.  thanks a ton.

---

### Post by pieterjanvu on 2008-01-03
Had the same problem, no boot splash
I found this posting by shyron that helped me out setting the resolution and it fixed the problem.
[http://ubuntuforums.org/showthread.php?t=618523](http://ubuntuforums.org/showthread.php?t=618523)

Add vesafb and fbcon in /etc/initramfs-tools/modules
then in : /etc/modprobe.d/blacklist-framebuffer , comment vesafb.  this means put "#" before vesafb
Finally in /etc/modules, add vesafb

Additionally I added vga=792 in the menu.lst after "kernel ...ro quiet splash"
gedit /boot/menu.lst

and
Changed usplash resolution to xres=1024 and yres=768
sudo gedit /etc/usplash.conf

Finall update usplash
sudo update-initramfs -u -k `uname -r`

---

