---
title: "Video Mode not Supported?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by l0k1_ on 2007-01-26
I recently installed Edgy and everytime I boot it up it says 'Video Mode not Supported'. But after that the OS boots up just fine. Should I be concerned about this? I tried installing the ATI driver using EasyUbuntu and it went through ... although I'm not sure how to configure it...

---

### Post by taurus on 2007-01-26
What's the entry for the kernel in /boot/grub/menu.lst?

Applications -> Accessories -> Terminal
```
cat /boot/grub/menu.lst
```

---

### Post by l0k1_ on 2007-01-26
title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda2 ro quiet sp lash
initrd          /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

---

### Post by taurus on 2007-01-26
You have an extra space between **sp** and **lash**!  So, edit /boot/grub/menu.lst and remove that space.

```
gksudo gedit /boot/grub/menu.lst
```
```

title Ubuntu, kernel 2.6.15-27-amd64-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/hda2 ro quiet **splash**
initrd /boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

```

---

### Post by l0k1_ on 2007-01-26
Thanks for noticing that - but that was just a case where the window wasn't maximized and the splash got cut off. Does this have to do with my video card? I tried running aticonfig but this is what I get:

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

---

### Post by ChrisG_UK on 2007-02-11
Hi,
I had exactly the same problem with Warty. SiS 6326 video card (supports VESA 2.0) with Dell E151FPp monitor which supports up to 1024x768. During boot the monitor complains it can't display the mode.

I changed my /boot/grub/menu.lst to include the vga parameter as follows:

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hde1 ro vga=788 quiet splash

I found a list of those vga numbers here:
[http://ubuntuforums.org/showthread.php?t=334995&page=2](http://ubuntuforums.org/showthread.php?t=334995&page=2)

vga=788 says 800x600x16bit. I should be able to use vga=791 (1024x768x16bit) but that also gave me the undisplayable video mode.

With vga=788 I get a blank screen during the boot (no splash), but the monitor is happy. Once booted the system goes into 1024x768. I still get the undisplayable mode when I shut down.

Anyone know what is going on here and how to fix it properly?

---

### Post by Xappe on 2007-02-11
I would try this:
Remove the vga option from the kernel entries, and check your /etc/usplash.conf and try to set a common resolution (like 1024x768 or 1280x1024) in that file...

---

### Post by ChrisG_UK on 2007-02-17
Thanks for that. usplash.conf was already at 1024x768, which definitely works for my system. I tried a few other resolutions just in case but no luck. By the way I'm using Edgy not Warty, sorry for the wrong info.

Any other ideas gratefully received. I will keep going with this until I find an answer and then I will post it here.

---

### Post by ChrisG_UK on 2007-02-18
Thanks Xappe for pointing me at usplash.conf

What has eventually done the trick for me is this:

Change /etc/usplash.conf to 800x600

In Terminal: sudo dpkg-reconfigure linux-image-`uname -r`

That rattled around doing stuff for a while, including completely overwriting my /boot/grub/menu.lst (including my Windows boot stuff - thanks a bunch!). Anyway, it now does not have any vga= parameter on the kernel command.

Now I get the nice splash screen and progress bar during boot and shutdown. At some point the system switches into 1024x768 and everything is happy.

There is a remaining question about why I have to use 800x600 for the splash, when the system happily supports 1024x768 when it's up and running. This whole splash thing seems a bit flaky. If anyone wants me to try out any other solutions let me know. I'm subscribed to this thread.

---

### Post by Xappe on 2007-02-19
I have another tip for you: If you add entries to your grub menu that you don't want the system to touch during reconfigurations and kernel updates, always make sure they sit before or after the debian automagic kernel list, that is;

Before:

### BEGIN AUTOMAGIC KERNELS LIST

and after:

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Xappe on 2007-02-19
and btw, did you try the 1024x768 option without the vga= entries in menu.lst?

---

### Post by ChrisG_UK on 2007-02-19
Aha - that will be very useful - thank you!

---

### Post by ChrisG_UK on 2007-02-19
Sounds crazy doesn't it? So I tried one more time to make sure. I changed usplash.conf to 1024x768, ran the dpkg-reconfigure, and re-booted. Sure enough I got the undisplayable video mode during shutdown and boot.

Changed usplash.conf to 800x600, ran dpkg-reconfigure, and all is well again. Nice splash during shutdown and boot, and the system comes up in 1024x768.

Although I no longer have a problem I need to fix, it would be interesting to know what's going on here.

---

### Post by Xappe on 2007-02-19
I would guess that it's the frambuffer driver that cant display in higher resolutions than just 800x600, but that's just a guess, since I'm not too familiar with basic display drivers and such...

I'm running my usplash at 1280x1024 myself, without any problems.

---

