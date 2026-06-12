---
title: "New monitor - wont boot"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by monkey56657 on 2008-02-18
Hello. I recently purchased a new monitor but cant get Ubuntu to boot with it hooked up (live CD doesnt work either). 

With my old monitor I can boot up ubuntu, reconnect the new monitor and then restart X (Ctrl + Alt + Backspace) and then my new monitor works fine. 

Any idea why it wont boot with new monitor?

I also have a problem with no display during the actual booting process (see link below) which stops me being able to read any error message being displayed (on any of the screens). 

When in ubuntu everything is fine using Nvidia restricted drivers. 

Thanks for your help..

The other thread. [http://ubuntuforums.org/showthread.php?p=4249065](http://ubuntuforums.org/showthread.php?p=4249065)

---

### Post by sabatron on 2008-02-18
I don't know much about hardware, but don't monitors usually come with installation CD's?  I had the same problem but all I did was install my monitor in Windows XP and then boot back into Ubuntu and it worked fine.

---

### Post by Charcoal1981 on 2008-02-18
If you have not previously manually edited your xorg.conf file you could try the following whilst you have the new monitor attached (I am right in thinking you can get it to work if you start with the old one and then switch over yes?)

```
sudo dpkg-reconfigure xserver-xorg
``` 

Make sure you make a back-up copy of your xorg.conf before trying this in case something horrible happens ;)

If this doesn't work post the contents of your xorg.conf file and give some info on your new monitor make and model.

---

### Post by monkey56657 on 2008-02-20
I tried this and am still left with the same problem.

---

### Post by monkey56657 on 2008-02-20
Okay so I simply connected the monitor with both a VGA and a DVI cable. 

And enabled dual monitor using Envy + Some other stuff from a guide. 

I still get no display during boot but I can get on new monitor.

---

### Post by Charcoal1981 on 2008-02-20
When does the display cut off/on during boot? do you get to see the bios checks etc?

---

### Post by mivo on 2008-02-20
If I understand this correctly, you get a blank screen during the boot procedure, but the monitor displays something again when you are prompted to log in?

If so, you can add the option *nosplash* to Grub's boot options, and remove *quiet* from the options, and see if that helps. This is done in /boot/grub/menu.lst (you can also test this by interrupting Grub and changing the boot options).

However, normally the monitor should not have an impact on this (only the video card). Hmm, unless perhaps you have a VGA option in /boot/grub/menu.lst that isn't supported by the monitor at all. I'm not sure what this would do, though.

---

### Post by monkey56657 on 2008-02-20
Well it always works if VGA is set as the primary card. But thanks for the tips about disabling splash.. 

Maybe with a text based GUI can see what the problem actually is :)

Will get back to you tomorrow.

---

