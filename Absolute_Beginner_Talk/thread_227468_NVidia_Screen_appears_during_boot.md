---
title: "NVidia Screen appears during boot"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-01
Hi
After I installed the 3d accelerator for my Nvidia GeForce 420X card, a full screen NVidia display appears briefly just before the user login page on boot up.
Although I have no problem with NVidia, I really don't need to prolong the boot by a few seconds just to be reminded that I have one of their video cards.
Can anybody help me get rid of this display?

Thanks
Paul

---

### Post by halfvolle melk on 2006-08-01
Hi,
Check this out:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
> Remove the nVidia logotype
If you want to get rid of the nVidia logotype that shows up before your login screen you need to perform some manual edits in the Xorg configuration file. 
Select the Applications menu at the top of the screen, then Accessories and then Terminal. 
Type the following: 
gksudo gedit /etc/X11/xorg.conf
Find the line Driver "nvidia" in the Device section 
Just after this line, add 
Option          "NoLogo"
Save the file and exit 
Close all your applications, then press Ctrl-Alt-Backspace to restart the X server. If the logotype is gone and everything seems to work you are done.

---

### Post by PaulFXH on 2006-08-02
Hi halfvolle melk  
That did the trick!!
Thanks for the advice

Paul

---

