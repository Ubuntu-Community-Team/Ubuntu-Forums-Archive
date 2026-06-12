---
title: "upsplash screen"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-12
Hi 

I've installed this upsplash : [http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468) and it doesn't work and now i would like to know how to uninstall it. Because i cannot even entry my 2.6.20-16 installation only my 2.6.20-15 installation because of that upsplash. So what do i do?

Really need help!

---

### Post by BobCFC on 2007-07-12
As a first step to boot the *.16 kernel you can edit the grub menu while booting by pressing **e** then choose kernel line and press **e** again.  Scroll to the right and change **spash** to **nosplash**

Press **escape** to go back and then **b** to boot. This will skip the image and just do text boot this time.

Now to uninstall, first how did you install the usplash?  For me I used a program called startupmanager to install the usplash-theme-fingerprint and I can use the same program to go back to the usplash-theme-ubuntu on the appearance tab.

```
gksudo startupmanager
```

Or whatever program you used before.

If you still get really stuck and want to skip the splash every time without pressing e then edit the grub file to **nosplash**
```

gksudo gedit /boot/grub/menu.lst  
```

---

### Post by czepluch on 2007-07-13
> **BobCFC said:**
> As a first step to boot the *.16 kernel you can edit the grub menu while booting by pressing **e** then choose kernel line and press **e** again.  Scroll to the right and change **spash** to **nosplash**

Press **escape** to go back and then **b** to boot. This will skip the image and just do text boot this time.
 
Now to uninstall, first how did you install the usplash?  For me I used a program called startupmanager to install the usplash-theme-fingerprint and I can use the same program to go back to the usplash-theme-ubuntu on the appearance tab.

```
gksudo startupmanager
```

Or whatever program you used before.

If you still get really stuck and want to skip the splash every time without pressing e then edit the grub file to **nosplash**
```

gksudo gedit /boot/grub/menu.lst  
```


.

Now ive got a new problem - when i try to boot in 2.6.20-16 it says : waiting for root file system.
What is that about and how do i make it go away?

---

### Post by BobCFC on 2007-07-13
What happens when you select 2.6.20-16 **Recovery Mode**... this should give you a more specific message about what is failing  Maybe something juicy to paste into google?

---

