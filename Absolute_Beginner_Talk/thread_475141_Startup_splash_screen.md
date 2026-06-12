---
title: "Startup splash screen"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-15
Hey!

I'm getting a LITTLE annoyed by the Ubuntu splash screen. Is there any way I can modify it/change it/delete it along with the sound?

---

### Post by Bachstelze on 2007-06-15
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by alecwh on 2007-06-15
I read through that, but I still have no idea how to do it. I'm fairly new to Linux, and I'm not sure how you would remove it.

---

### Post by drs305 on 2007-06-15
You can run this line in terminal to stop ubuntu splash screens:
```
gconftool-2 set /apps/gnome-session/options/show_splash_screen false
```

To do it graphically or to change the splash screen, open gconf-editor and find apps>gnome-session>options  Uncheck/check show_splash_screen and there is another option to set the splash_image.

You can turn off the initial sounds (and others) through System, Preferences, Sound, Sounds

---

### Post by kpkeerthi on 2007-06-15
If you want get rid of BOOT SPLASH...

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```

Locate the line that reads the kernel version you see in your BOOT MENU that appears similar to  
```

kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash

```
and change to (Remove the word splash from the line)
```

kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet

```

---

### Post by alecwh on 2007-06-15
Thanks, that worked.

kpkeeri, I'll use that in the future, it might come in handy. Thanks!

---

