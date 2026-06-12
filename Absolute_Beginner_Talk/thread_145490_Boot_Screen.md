---
title: "Boot Screen"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-16
Is it possible to change this? I've looked on gnome-look but unsure of what it might be called **if ** it can be changed.

I mean the screen you see after Grub.

---

### Post by Harry_Sack on 2006-03-16
I know it can be done.
If you install xubuntu-desktop, you'll get a nice xubuntu one.
You can disable it by doing in terminal:

```
sudo gedit /boot/grub/menu.lst
```

Then scroll down to below ## ## End Default Options ##

For each of the kernels there are several lines with information
Look at the one starting with "kernel" (without the quotes).

Remove the word "splash" at the end of that line.

That's how you (I) remove it.
Sadly, it comes back for some reason, when ever grub updates itself.
Haven't looked into this though.

I think you can find more un the ubuntu wiki.

Maybe this is what you're looking for?

[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

Aha, found this [http://www.ubuntuforums.org/showpost.php?p=829263&postcount=2](http://www.ubuntuforums.org/showpost.php?p=829263&postcount=2)

and this [http://www.ubuntuforums.org/showthread.php?t=82835&highlight=usplash](http://www.ubuntuforums.org/showthread.php?t=82835&highlight=usplash)

---

