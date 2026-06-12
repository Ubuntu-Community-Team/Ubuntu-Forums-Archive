---
title: "Stuck in 1024x768, 0Hz refersh rate?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by mdeasy on 2006-11-12
I want to get my resolution up on my 17" screen, but I'm stuck in 1024x768 with a 0Hz refresh rate. In order to get my computer to work with Ubuntu, I had to change what it said my video card was somewhere. It was a long time ago, so I forget what I did.
My video card: Integrated Intel Graphics Media Accelerator 950

---

### Post by joshsherman on 2006-11-14
Not sure if you're having issues booting up or if it's when you're running X.

If it's when you're running X you would need to configure your card in /etc/X11/xorg.conf (you can set the refresh rate and and the resolutions as well).

Not sure what driver would be necessary for your card, you'll have to research that.  On my old laptop I had some sort of integrated Intel chipset, and I used 'i810' and it worked nicely (even had Compiz running)

-j

---

### Post by lazyart on 2006-11-14
sudo dpkg-reconfigure xserver-xorg

You can step through and reset your stuff that way... it's the same as editing the xorg.conf file but it will walk you through it all.  Reboot and you should be good.

---

### Post by marx2k on 2006-11-14
As an aside, what does a 0Hz refresh rate look like?!

---

### Post by bodhi.zazen on 2006-11-14
> **mdeasy said:**
> I want to get my resolution up on my 17" screen, but I'm stuck in 1024x768 with a 0Hz refresh rate. In order to get my computer to work with Ubuntu, I had to change what it said my video card was somewhere. It was a long time ago, so I forget what I did.
My video card: Integrated Intel Graphics Media Accelerator 950

Try installing 915resolution.

for a how-to see this post, near the bottom: [915resoloution](http://ubuntuforums.org/showthread.php?t=269052)

---

