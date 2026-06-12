---
title: "new themes?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by SandeshM on 2006-09-19
I tried installing some new themes from gnome-look.org, but I havent been able to get any of them to work. I'vd tried things from the GTK 2.x but have been unable to add any of them to the Theme Preferences window, even when they are specifically marked as Ubuntu Packages.
Are there any steps to take to install specific themes, or better resources for them?

Thanks in advance!

---

### Post by jordanmthomas on 2006-09-19
If you get one that is a .deb, just download it to your Desktop and then double click it.
If it's a tarball (*.tar.*), double click it and drag the folder into ~/.themes

---

### Post by SandeshM on 2006-09-19
how do i get to ~/.themes?
is that the full directory path?

---

### Post by jordanmthomas on 2006-09-19
You can open up your home folder and press <Ctrl>L so you can type the address
Type ~/.themes
just as it says.  A file with a . at the start is hidden, so you can also press <Ctrl>H in nautilus (the file manager) to see it.
The ~ just stands for your home directory.

After you put the contents of the tarball in there, the theme will be available in the theme manager.

---

### Post by Neobuntu on 2006-09-19
Um, can't you just drag the theme file onto the theme manager in ubuntu? It will ask you if you would like it installed. Note that you may have to select theme details to see your desired result.

Also, Gnome art or whatever it's called, once installed, lets you install theme's and more.

Yet, I use KDE. I just install the (KDE) .deb theme like "Baghira" and set it to my liking.

P.S. I also found installing and using gtk "switch" and "switch2" helped some themes do more (change the look of the taskbar too). I don't understand why, perhaps someone could explain that to me.

I do note that there are kind of four theme settings. KDE user for QT program and then the KDE theme also for root so that programs like Synaptic with also change. Then Gnome gtk themes for user and likewise for root gtk programs. I had to copy the theme and icon folders (Including my new addition from the net) to the /root directory and set files to root permissions for the GTK themes I added from the net.

I once acheived a unified Mac look with MacOS-X for Gnome and Baghira for KDE and some scanline look adjustments. With doing root too, everything matched. Yet, if you have regular different themes you can tell which you are running. It's all looks; everything works.

Remember though, with all this complicated stuff, all one needs to do with ubuntu is select from one of the preinstalled themes and everything (user) changes over to it instantly. It takes about two seconds. So it's very user friendly. Clearlooks is a good diversion from the brown. Just click it and see. That's it.

---

### Post by jordanmthomas on 2006-09-19
I thought SandeshM was referring to themes that  be called invalid by the theme manager.  Hence, the need to extract them manually.

---

### Post by Brunellus on 2006-09-19
1) install the gnome art manager

sudo aptitude install gnome-art

2) run gnome-art

3) use gnome-art to install the themes

---

