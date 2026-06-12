---
title: "Splash screen???"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-09-14
I want to change my splash screen logo.....been looking through the threads but cannot find anything....can anyone please send me in the right direction.

thanks

---

### Post by Najand on 2006-09-14
Which splash?
Grub Splash, Boot Splash or Login screen?

---

### Post by soutSA on 2006-09-14
I just want to change the logon screen and if posible the logon prompt that you get after you locked your screen.

can you change your boot splash and grub splash? how do you do that?

thanks in advance

---

### Post by Tomosaur on 2006-09-14
You can change all of these. The login prompt is easy to change, just go to System > Administration > Login Window (on Gnome at least) and you can change what it looks like through there. The usplash is slightly more tricky, there's a thread about it somewhere, just do a search for 'change usplash' or something. The grub splash screen requires you to make an image with a specific number of colours at a low resolution. You need to alter your /boot/grub/menu.lst file and add a line to it so that it knows where to find the splash image. The line you should add is:
```

splashimage (hd0,1)/boot/grub/images/splash.xpm.gz

```

But obviously, change that to reflect your settings. You can also download the script in my sig, it has the ability to set up a splash screen for you.

---

### Post by Najand on 2006-09-14
Yoou can also find information about boot splash at Ubuntu documentation:
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

---

