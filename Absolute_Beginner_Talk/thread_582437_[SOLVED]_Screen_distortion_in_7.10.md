---
title: "[SOLVED] Screen distortion in 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by hung0702 on 2007-10-19
[FONT="Trebuchet MS"]Hey everyone, I'm having a problem with 7.10. 7.04 was doing fine, but I made the mistake of falling for the hype and upgraded to 7.10. Jeez. I was planning to wait a few months for all the bugs to be worked out, but it was so enticing, the "Upgrade to 7.10" button in the Update Manager.

My problem is strange screen distortion. When I boot and it shows the log-in screen and everything is fine (albeit it's only in 800x600 mode because I couldn't figure for the life of me how to fix it like in 7.04, since the xorg.conf was fixed). When logged in, the screen gets some strange distortion pattern. All the pixels are still there, I think, but all the horizontal rows are shifted. Imagine a regular window, but every other set of 2 pixels is inverted or shifted to the right or something, I don't really know the specifics. I can't upload a screenshot because the distortion has rendered it unnavigable. I'm pretty sure this has something to do with the GUI xorg.conf. Thanks Gutsy Gibbon. I set it the generic 1680x1050 setting and used 60 Hz, which is what I used on 7.04, because it didn't detect my HP w22. I also tried to enable nvidia drivers&#8212;"vesa" or something&#8212;for my 7500 LE.

Is there some way I could log-in but in safe-mode? I'm dual-booting with Vista (only for business and printing, I swear) and I'm using the Vista Bootmanager to load Ubuntu. Thus, GRUB is passed over and I can't choose to boot in safe-mode. If someone could help me, I'd be really grateful. I don't want to leave Ubuntu. It's grown on me. Please help.


P.S. I'm looking to revert to 7.04, but I'm not going link it here since it's against forum rules, but you can find it in the install/upgrade section.[/FONT]

---

### Post by Sturmeh on 2007-10-19
I had the same problem myself for some length of time...

Except it's not complete distortion, more like the occasional tear in my gfx.

I think there's something severly wrong with power management in gutsy, you aren't using a laptop on AC power by any chance are you?

It could have been compiz, because the screen tearing stopped as soon as i started to use compiz.

---

### Post by Thunar on 2007-10-19
7.10? 

Wow where have I been? I had no idea.

Well it sounds like your resolution is set wrong, so maybe your xorg.conf file may not be correctly configured. And unfortunately if grub is passed over then safe mode wont happen there. However you can try this:

After you log in and get the distortion switch to console mode (ctrl+alt+F1), login and type this command :

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

to reconfigure your X server.

Then back to to X (ctrl+alt+F7) and restart X (ctrl+alt+backspace)

I hope this works for you!

---

### Post by Thunar on 2007-10-20
You know, I hear something about gutsy needing compiz, idk if that's true or not, but if it's already installed you can just start 'Run Application' (ALT-F2) and type in 

```

compiz --replace

```

and that should start it up.

I don't know if this is necessary though, because I think Compiz is is installed by default on 7.10, and therefor probably enabled by default.

The other problem you may be having is the driver, you may need to install the proprietary Nvidia driver. You can either do this using the restricted drivers manager, which you probably don't have access to thanks to your scrambled screen, or you can go into console mode (ctrl+alt+F1) and install it from there:

```

sudo apt-get install nvidia-glx-new

```

then:

```

sudo nvidia-xconfig

```

to enable it.

If this doesn't work for you and you decide you want to uninstall the proprietary driver (which I wouldn't, but you may want to), you can do this:

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

to backup your configuration file, then:

```

sudo apt-get --purge remove nvidia-glx-new

```

to remove the driver. If you're in console go back to X (ctrl+alt+F7), then Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver).

hope this helps!

---

### Post by JohnSGruber on 2007-10-20
If you are going to install an nvidia-glx package you need to pick which one. The oldest cards are supported by nvidia-glx-legacy, the next oldest by nvidia-glx, and the newest by nvidia-glx-new. The restricted driver manager figures out which one you need, if I recall correctly.

---

### Post by JohnSGruber on 2007-10-20
hung0702:

Regarding a safe-mode way to logon, have you tried a fail-safe gnome session? If you would like to try this go to the session menu on the bottom left of the logon screen and select it, then try to logon again. If you don't see the session menu you may have to move your cursor to the bottom left of the screen to make the image move into view.

---

### Post by Thunar on 2007-10-20
> **JohnSGruber said:**
> If you are going to install an nvidia-glx package you need to pick which one. The oldest cards are supported by nvidia-glx-legacy, the next oldest by nvidia-glx, and the newest by nvidia-glx-new. The restricted driver manager figures out which one you need, if I recall correctly.

This is true, but I noticed hung0702 mentioned his card was a 7500LE, and I'm fairly certain this falls into the 'nvidia-glx-new' category. Plus, I was assuming from hung0702's original post that he was having trouble navigating in X, which would make using the Restricted Drivers Manager difficult. But this is a good point.

As for me I installed my Nvidia drivers for my FX5200 using the very same commands I mentioned above, and I have had no problems whatsoever. Beryl, Wine, everything works great. So I tend to prefer that method.

Of course, I use 7.04, not 7.10, so can't be 100% how well it will work out for a 7.10 user.

---

