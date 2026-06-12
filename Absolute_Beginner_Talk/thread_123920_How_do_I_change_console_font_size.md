---
title: "How do I change console font size?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by chugru on 2006-01-31
When working in console mode, my text font is too large. Is there a way to make it smaller? (It's ok in X windows.)

Thanks!

---

### Post by gooner on 2006-01-31
Edit > Current profile > General tab > Uncheck "use the system terminal font" and then click on the box next to font: and set your font size and style.

---

### Post by mcduck on 2006-01-31
You mean in CLI, not in terminal?

It's not about font size, but display resolution.

Edit your /boot/grub/menu.lst and add vga=792 to the end of your Ubuntu kernel line. (792 for 1024*768, google for more codes if that doesn't fit your setup.)

You'll loose the cool graphical ubuntu boot and get traditional text-boot instead though.

---

### Post by chugru on 2006-01-31
**mcduck wrote:**> You mean in CLI, not in terminal?


Yes, I do mean in CLI, but I don't want to lose the> cool graphical ubuntu boot

Is there not a way to temporarily change font size using CLI??

Thanks...

---

### Post by ardchoille on 2006-01-31
[QUOTE=mcduck]You mean in CLI, not in terminal?

It's not about font size, but display resolution.

Edit your /boot/grub/menu.lst and add vga=792 to the end of your Ubuntu kernel line. (792 for 1024*768, google for more codes if that doesn't fit your setup.)

You'll loose the cool graphical ubuntu boot and get traditional text-boot instead though.[/QUOTE]
I use vga=791 and I have a nice screen in my tty's. I also still have the Ubuntu boot screen instead of text mode, changing the vga= in menu.lst doesn't get rid of the Ubuntu boot screen.

---

### Post by SilentCacophony on 2006-01-31
I prefer the **vga=794** option (I think it's 1280x1024, not sure though.) My usplash works fine with that, simply displaying the graphics smaller and centered on the screen. Actually looks more pleasant to me, with less visible pixelization.

I have, however, recompiled my usplash from the original package. I don't know if that makes a difference.

I would imagine that you could simply remove the vga option to revert it, so there should be no harm in trying it.

---

### Post by mcduck on 2006-01-31
[QUOTE=ardchoille]I use vga=791 and I have a nice screen in my tty's. I also still have the Ubuntu boot screen instead of text mode, changing the vga= in menu.lst doesn't get rid of the Ubuntu boot screen.[/QUOTE]
I remember having problems with that, but I think I'll try again. :)

Here's a table of different resolutions:
```

                640x480 800x600 1024x768 1280x1024 1600x1200
---------------+-------+-------+--------+---------+---------
256 (8 bit)    |  769     771     773       775       796
32,768 (15 bit)|  784     787     790       793       797
65,536 (16 bit)|  785     788     791       794       798
16.8M (24 bit) |  786     789     792       795       799

```

---

### Post by chugru on 2006-01-31
**mcduck wrote:**> 
Edit your /boot/grub/menu.lst and add vga=792 to the end of your Ubuntu kernel line. (792 for 1024*768, google for more codes if that doesn't fit your setup.)

You'll loose the cool graphical ubuntu boot and get traditional text-boot instead though. 

Finally, back at my Breezy box, I tried the grub vga settings suggested above. Unfortunately, mcduck's post was correct... no splash during boot.

There must be some additional tweaking that would get both the splash and the higher resolution working in unison... :???:

---

### Post by mcduck on 2006-02-01
[QUOTE=chugru]**mcduck wrote:**

Finally, back at my Breezy box, I tried the grub vga settings suggested above. Unfortunately, mcduck's post was correct... no splash during boot.

There must be some additional tweaking that would get both the splash and the higher resolution working in unison... :???:[/QUOTE]
I tried it again, and now it indeed works for me :) The graphical boot is *very* tiny, but I can live with that.

But you could try some different resolutions or color depths. If I remember right, using 'vga=ask' should give you a list of supported modes.

---

### Post by ardchoille on 2006-02-01
[QUOTE=mcduck]I remember having problems with that, but I think I'll try again. :)

Here's a table of different resolutions:
```

                640x480 800x600 1024x768 1280x1024 1600x1200
---------------+-------+-------+--------+---------+---------
256 (8 bit)    |  769     771     773       775       796
32,768 (15 bit)|  784     787     790       793       797
65,536 (16 bit)|  785     788     791       794       798
16.8M (24 bit) |  786     789     792       795       799

```[/QUOTE]
A million thank you's for posting this table. Much appreciated :)

---

### Post by chugru on 2006-02-02
After a full day of trying each and every grub vga setting, I find none of the settings to permit usplash...

For every entry in the grub kernel line using "vga=": **/boot/initrd.img-2.6.12-9-386** fails to load, giving the following error: ```
insmod: can't read '/lib/modules/2.6.12-9-386/initrd/vesafb.ko': No such file or directory
```

If I omit "vga=" in grub, usplash once again works. :???:

Seems as if grub is not handling the "vga=" setting, eg:```
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash vga=771
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

```

Are there any suggestions as to what else I might try?

Thanks...

---

### Post by jrchan on 2008-02-13
Hi

I recommend you read te next page:
[http://spblinux.de/2.0/grub.htm](http://spblinux.de/2.0/grub.htm)

Expect help!

---

