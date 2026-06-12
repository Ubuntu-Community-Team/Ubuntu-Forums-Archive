---
title: "New to linux, need help with screen resolution"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by wack206 on 2006-06-20
I just installed Ubuntu today and I'm having trouble adjusting the screen resolution.  Currently it is set to 640x480 and when I go to screen resolution settings I am unable to change that.

The system is now set to dual boot and my windows option allows me to change resolution much higher than that.  Is there a driver I'm missing and if so how do I go about obtaining it and installing it properly?

Any help is greatly appreciated.
Thanks

---

### Post by IYY on 2006-06-20
It didn't detect the avaliable resolutions correctly. You could try running this:

```
sudo dpkg-reconfigure xserver-xorg
```

If it doesn't work, manually edit the file located at /etc/X11/xorg.conf (in the command line: sudo nano /etc/X11/xorg.conf) and add the resolutions you want.

---

### Post by Jasper Houtman on 2006-06-20
Your display adapter is probably set to standard Vesa.
in the terminal type: 

sudo dpkg-reconfigure xserver-xorg

Select your video card and set it up.
then type:

sudo /etc/init.d/gdm restart

Should work fine after that.

---

### Post by houstonbofh on 2006-06-21
Also, if you have settings selected that your display can not actually display, it will default to VGA.  That is a problem with these old Compaq servers I have been working on.  You have to limit everything to 8 bit in xorg.conf.

---

