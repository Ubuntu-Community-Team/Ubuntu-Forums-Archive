---
title: "Blank screen until gnome"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by McHenry on 2006-10-16
When I switch on the computer I see some initial messages then the screen blanks, monitor reports no signal, then the screen comes back to life when gnome loads ?

How can I resolve this as it is misleading and users reboot the pc before gnome loads thinking somethng is wrong.

Thanks

---

### Post by ciscosurfer on 2006-10-17
You can go into your */boot/grub/menu.lst* file and modify your kernel line like so, adding ***vga=791*** to the end (ignore the preceding text, just add vga=791 to the end of your line -- this corresponds to [SIZE=-1]VESA framebuffer console @ 1024x768x64k [[you can modify this to your liking by visiting this site]("http://www.theevilpixel.com/?q=node/272")]```
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro quiet splash **vga=791**
```To have this permanently set, i.e., to retain this setting even after a kernel upgrade, and what I would advise you to do anyhow, is to set the vga= code here, adding vga=791 or whichever framebuffer mode you'd like  to the end of this line, like so, also located in your /boot/grub/menu.lst file:```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **vga=791**
```DO NOT REMOVE THE # BEFORE THE LINE, IT IS SUPPOSED TO BE THERE!  

If you choose the first option, after you've added the framebuffer code, save the file and then reboot.

If you choose the second option (recommended), after you've added the framebuffer code, save the file then go into a terminal and type```
sudo update-grub
```Let it do its thing, then reboot.

Then you're all set!

Hope this helps!  Happy tweaking! ;)
[/SIZE]

---

### Post by dmizer on 2006-10-17
humm ... not sure, but posting the output of dmesg might shed some light on the problem.  what kind of monitor is it?  connection type?

---

### Post by McHenry on 2006-10-17
It's a Dell 17" flat screen.

I had to change xorg.conf to use Radeon instead of Ati in order for X to work so I'm not sure if this is related or not.

Thanks

---

