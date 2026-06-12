---
title: "Ubuntu 6.06 Server - CLI change VGA mode"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Rainmaker_mail on 2006-08-01
Dear all,
I've installed Ubuntu LTS Server on my dell XP (running Virtual PC 2004). Everything okay except when it boot - the video mode is out (text too big). I reboot the system and choose recovery mode and the text size is okay.

I am looking for how to change the video mode during normal boot. Btw i did not install any desktop (so can't edit /etc/X11/xorg.conf) and my /etc/default does not have 915resolution. Which file should i edit?

Can anyone help me? 

Many thanks,
RM

---

### Post by Indras on 2006-08-01
The CLI VGA mode is set by parameters sent to the kernel with grub.

Open your menu.lst file:
```
sudo nano /boot/grub/menu.lst
```

And find the entry you normally use to boot with and go to the line that begins with "kernel", it should say something like this:
```
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
```

Add a "vga=" option to the end of the line, and go to this page: [http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html).  Go to section 5.3 and look up your desired resolution and bit depth in the table.

So if you want 1280x1024 at 16 bit color at command line, add "vga=0x31A" to the end of your kernel parameters.

This will also change the resolution of your usplash screen (if you have one).

Normally, when you upgrade your kernel or run grub-reconfigure, it will remove this option and set it back to defaults.  In order to make this change permanent, go up a couple lines to one that looks like this:

```
# defoptions=quiet splash
```
(yes, it's commented out, but grub-reconfigure looks for this (and other) commented-out options when rebuilding your grub menu)

And add the vga= option to the end of that as well.

---

### Post by Rainmaker_mail on 2006-08-01
Dear Indras,
Thanks!. It works.:D Appreciate your kind assistance.

This forum is awesome!

Cheers,
RM

---

### Post by jis on 2008-03-28
Indras, the link you gave is not working. I made a clean upgrade from Dapper to Gutsy, command line system to be strict. Now if I add the same mode that I used with Dapper (namely vga=0x315), I get blank screen after grub. Without a vga parameter the screen works, but with low resolution, I suppose it is 640x480. I am also using  nosplash parameter.

---

