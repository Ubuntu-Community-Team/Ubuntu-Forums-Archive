---
title: "screen resolution question..."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by iPirates on 2007-01-18
Is there any way to change the native screen resolution (from when the computer boots up?).

My problem, is that every time I boot my computer up, it boots up in 1600x1050 resolution, and I only have a 17' monitor... so you can see my problem.   Every time Ubuntu loads, I have to change the resolution down to 1024x786... how can I fix this?

---

### Post by mcduck on 2007-01-18
for boot, you can add 'vga=791' in /boot/grub/menu.lst after the kernel line to force boot in 1024x768.

For X, you could just remove all other resolutions from /etc/X11/xorg.conf..

---

### Post by deadowl on 2007-01-21
My computer boots without it's native resolution for some reason... 1680x1050
I actually have tried removing all other resolutions from xorg.conf. However, when I go to preference I get all the other resolutions still, and it never has 1680x1050 unless I restart x.

Very confusing.

---

### Post by wpshooter on 2007-01-21
The way I would do this would be to install Ubuntu using the ALTERNATE CD version which lets you choose whichever resolutions that you want to be available.

---

### Post by jonny on 2007-01-21
```
sudo dpkg-reconfigure xserver-xorg
```
When you're presented with a list of availalble resolutions, deselect 1600x1200

---

### Post by Blofeld on 2007-01-21
Awsome, that did it for me, too!  Finally my box doesn't look like it's running Windows For The Visually Challenged ...
Was a lot of work though. ;)
Thanks, folks.

---

### Post by iPirates on 2007-01-24
Yea thanks, that works

---

