---
title: "xorg.conf error - edgy"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by sagesa on 2007-01-23
hi all

After running the update program for edgy I cannot boot into the operating system - it gets to  the point of the Nvidia driver splash screen (it's a TNT2 M64 card), then reports an error with xorg.conf (cannot load X etc...)  I have a backup copy of xorg.conf on my desktop - only problem is I have no idea how to replace the one in /etc/x11/ with the backup if I cant get into the GUI!  Sorry, very new to all of this :( 

Thanks :)

---

### Post by pay on 2007-01-23
Boot into the recovery console and type (after putting in your username and password) ```
sudo cp -r /home/<user>/Desktop/xorg.conf /etc/X11/xorg.conf
```

---

### Post by kvonb on 2007-01-23
Sounds like you will have to re-install the Nvidia driver, I assume that you are using the official one from the Nvidia website?

Each time a kernel update, or a restricted-modules update comes along you will have to re-install the driver because it needs to re-compile a new version of the nvidia kernel module.


All you have to do is locate the Nvidia driver and run it to re-install it.

If you need instructions, look here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Scroll down to _**Step2/Option2**_, follow the instructions but replace the driver version with the version you have.

Regards, KEv :)

---

### Post by sagesa on 2007-01-23
Thank you - my foray into windows to post the problem has left me somewhat shaken.

I got edgy running on the backup xorg.conf and will tinker with the driver :D

---

