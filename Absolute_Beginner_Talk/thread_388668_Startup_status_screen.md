---
title: "Startup status screen?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Qwertinsky on 2007-03-19
I just upgrades my latop to Edgy using the synaptic upgrade method.

Now when I start linux the screen goes blank except for a flashing curser for what seems to be a long time befor the login screen comes up.

Now dapper had a Ubuntu logo with some information scrolling as the system startup progressed.

Is there any way to get something like that in edgy?

Even the standard text scrolling startup information that most other distro's have would be better than just a blank screen.

---

### Post by dmsynck on 2007-03-19
I think what you are looking for is called 'usplash'. If you do a search on that term in Synaptic, you should find the packages like usplash-theme-ubuntu', 'kde-artwork-usplash', etc.

---

### Post by Qwertinsky on 2007-03-20
I looked through synaptic and it says Upsplash is installed. I take it from the upsplash description that the frame buffer mode is not compataible with my laptop, as I said I only get a blank screen not the Ubuntu logo on startup.

So I was going to remove upsplash but to remove it synaptic also demands it removes the Ubuntu desktop :confused: 

Is there any way to remove Upsplash whthout removing the Ubuntu desktop?

---

### Post by mcduck on 2007-03-20
There are 2 things you could try. Either add 'vga=792' to your kernel line in /boot/grub/menu.lst to force Ubuntu to use 1024x768 resolution with 32bit colors when booting (which might make the splash work for you) or then remove 'quiet' and 'splash' from the same line to use the traditional text boot instead of the splash.

edit: removing the ubuntu-desktop package will not remove any programs or your desktop, it's just empty package that depends on all packages in default Ubuntu desktop install, but no package depends on it. So installing it will install Gnome + all default apps, removing it removes nothing else than the ubuntu-desktop package itself.

---

### Post by Qwertinsky on 2007-03-20
> **mcduck said:**
>  remove 'quiet' and 'splash' from the same line to use the traditional text boot instead of the splash.

that worked and it even boots faster now

Thanks!

---

