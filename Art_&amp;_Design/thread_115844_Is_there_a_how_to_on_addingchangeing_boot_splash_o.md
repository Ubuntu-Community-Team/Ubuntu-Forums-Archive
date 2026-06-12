---
title: "Is there a how to on adding/changeing boot splash on Ubuntu?"
date: 2006-01-11
forum: Art &amp; Design
---

### Post by Bandit on 2006-01-11
Hello Everyone,
I just updated my kernel and I was wondering if there was a how-to on adding or changing your boot splash on Ubuntu. I used to do it alot on SuSE, but I am looking for one more Ubuntu specific. I compiled/installed the new 2.6.15 kernel last night to help with stability issues on my new AMD64 system. Now I have a boaring black screen that shows up befor GDM loads.
I am looking to just have the normal boot screen scroll up the screen with a nice background behind it. Nothing to fancy.
If anyone can point me in the right direction that would be cool.
Thanks,
Bandit

---

### Post by seasponge on 2006-01-11
look in configuration editor. you can point to whatever image you want.

---

### Post by Bandit on 2006-01-11
Configuration editor?
I use the command line..

---

### Post by jaboua on 2006-01-11
[QUOTE=Bandit]Configuration editor?
I use the command line..[/QUOTE]
He probably thinks of the gnome/KDE splash screen, not the framebuffer splash. Myself I've never added a bootsplash, but if you google around you might find something. I think you need a kernel patch to be able to use a bootsplash at all, and make sure you have the VESA framebuffer driver compiled into your kernel.

---

### Post by tkjacobsen on 2006-01-11
sudo update-alternatives --config usplash-artwork.so

you also need the "splash" option in the kernel load command in /etc/grub/menu.lst

---

### Post by Bandit on 2006-01-11
I went home for lunch and check my kernel configuration. I didnt have frambuffer for boot spash enable.. Guess I over looked it.
I have the kernel compiling now so I will check it out this evening.
Cheers,
Bandit

---

### Post by endersshadow on 2006-01-11
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

Go nuts :-D

---

### Post by jpkotta on 2006-01-12
I realize that this is different, but I recently figured out how to add a splash to Grub.  Added this to the [GrubHowto Wiki page]("https://wiki.ubuntu.com/GrubHowto")

---

### Post by Bandit on 2006-01-12
Thanks Bookmarked it ;)

I am still having trouble installing the bootsplash. I think it has something to do with my kernel. I did configure everything. But even the default nvidia screen doesnt show, but on the old generic ubuntu kernel the usplash still shows.
I dont know.. This is the first kernel I ever built, but I know enough I am sure I did everything correctly. 
Ah hell I am always learning... I am sure I will figure it out..

---

### Post by jaboua on 2006-01-12
You have to reinstall the NVidia drivers if you recompile a kernel. If you look in /lib/modules, you'll see folders for the different kernels, the nvidia driver put a module suitable for your kernel in the right module-directory. After compiling a newer kernel, it'll look in a different folder in /lib/modules, and the nvidia driver has to be installed there.

About the vesa framebuffer drivers, I remember having some issues on it the first time I tried gentoo, you have to enable vesa framebuffer support, a set of compiled-in fonts and the option to pass the videomode at boot, don't remember the exact names and positions of the settings atm, check it in menuconfig/gconfig/whatever. Then, at the end of the "kernel" line of the grub, pass vga=771 (iirc) to get a 1024x768 framebuffer, google to find some other.

---

### Post by Bandit on 2006-01-16
I finally figured out what was wronge. I was building frame buffer support as a module and not directly into the kernel its self.
So everything works now..
Even got nVidia 8178 drivers install and working on my Athlon64 system w/GL support.
Thanks for the help everyone.
Cheers,
Bandit

---

