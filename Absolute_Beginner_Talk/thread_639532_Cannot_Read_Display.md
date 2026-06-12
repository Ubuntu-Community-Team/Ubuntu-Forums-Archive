---
title: "Cannot Read Display"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Wye Knott on 2007-12-13
Installed 7.10 using alternate cd (ISO) in Microsoft Virtual PC running under Windows XP on a brand new Dell Latitude D630 with NVIDIA Quadro NVS 135M display adapter.

Display can't be read.  I think Ubuntu has decided on excessive color depth -- like 24 bits/pixel or something like that.

I know there's a file I can edit but I don't know what it is.  I know there's a user-friendly editor but I don't know what that is either nor where the file is.

Since my display is unreadable, I've no idea how to do what's needed anyway.

Can anyone help?

Thanks,
Wye

---

### Post by Shinbu-Otaku on 2007-12-13
well generally the option is under System>Preferences>Screen Resolution, as it sounds like it may of set the hurtz of your screen too high. If you cant see that, i would suggest removing ubuntu and reinstalling it with a normal cd (not the alternate if possible), or just install it without installing it through windows (windows doesnt like helpful OS's lol)

---

### Post by Wye Knott on 2007-12-13
I HAD to use the alternate CD because I couldn't install with normal CD (I tried it).
I NEED a TEXT way to find the config file, fix the color-depth using some reasonable editor -- I know there's a user-friendly editor in ubuntu but I don't know its name.

I had this same problem in 7.04 but have forgotten how to fix it.

---

### Post by Thanoulis on 2007-12-13
Your file is /etc/X11/xorg.conf. If you aren't familiar with vi(m) try nano/pico or mined.
These are somewhat easier to use. 
Also i believe that what you need to enter your monitor's HorizSync/VertRefresh values under the section device.(You'll find them at your monitor's manual,or google for it)
Good luck ;)

---

### Post by Wye Knott on 2007-12-13
> **Thanoulis said:**
> Your file is /etc/X11/xorg.conf. If you aren't familiar with vi(m) try nano/pico or mined.
These are somewhat easier to use. 
Also i believe that what you need to enter your monitor's HorizSync/VertRefresh values under the section device.(You'll find them at your monitor's manual,or google for it)
Good luck ;)

Thanks.  That helped.  I had to drop the color depth down to 16 from 24.  That fixed the LCD screen.
(This is a laptop.)

Now if only I could get it to recognize the "mouse".
There's a touch-pad and also a bluetooth Microsoft Optical Mouse.
Neither is recognized.

---

