---
title: "Restore default graphics settings from Live CD?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by RoboBradley on 2008-03-08
Hello. I selected the wrong monitor in System ->Administration->Screens and Graphics, and now the screen is so screwed up I can't even make out any of the menu options to fix it! 

Since I was pointing and clicking, I didn't backup any files. My question is: can I restore the default graphics setting by booting from either the Recovery mode, or from the Live CD?

Thanks!

---

### Post by Rocket2DMn on 2008-03-08
You can into recovery mode and run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then reboot normally.

---

### Post by RoboBradley on 2008-03-09
> **Rocket2DMn said:**
> You can into recovery mode and run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then reboot normally.

Thanks for the quick reply. I ran that line in recovery mode, and rebooted. After the Ubuntu splash screen, my laptop monitor goes black and stays that way :(

I tried copying the file that gets created:

(cp xorg.conf.20080309000847 xorg.conf

 but the same result happens. I have an Nvidia card... maybe can I run 

sudo apt-get install nvidia-glx

from the live CD, or some such thing? I'm just afraid that anything I do from the live CD will not be permanent. Real newb here, sorry.

Thanks again

---

### Post by Rocket2DMn on 2008-03-09
If your GUI worked ok before, try running
```
dpkg-reconfigure xserver-xorg -phigh
``` from the recovery console and then reboot normally again, that should get your original settings back.  If it doesn't work, you can reconfigure X manually by this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you need the restricted drivers, enable those from System->Administration->Restricted Drivers Manager after you're back in the GUI

---

