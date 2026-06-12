---
title: "Chrash after Kernel Update"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by diskotek on 2007-03-27
I've already install ubuntu edgy eft to HP compaq nx7010 (with ati radeon mobility 9200).

everything was ok with installation. but after i made automatic updates i faced a problem. i logged on normally after gnome launchs and desktop appears, it turns to black screen and i faced again log-on screen. after gnome launchs and desktop appears for a while and says "there is already running gnome panel" and desktops appears without panels...

after the update i recognized that there is a new kernel on boot up. i've also tried to log on with older kernel; but again same things...  

how should i correct this, any idea?

---

### Post by Kobalt on 2007-03-27
I seems more like a conflict/problem with your xorg configuration rather than a kernel problem to me. 
Did you install some drivers for your graphic card ? 
I'd suggest you reconfigure X with this command line (you can press Ctrl+Alt+F1 then login to access a command line) :
```
sudo dpkg-reconfigure xserver-xorg
```
From there answer the questions (leave the default choice if you don't know what to pick) and then reboot. 
After that you should have a working session and you'll be able to resinstall properly your ATI drivers if you need to.

---

### Post by diskotek on 2007-03-27
thank you, it worked successfully, however now screen resolution got lower... 
now i'll try to install ati-drivers for it.

---

### Post by Kobalt on 2007-03-27
You can try to install the drivers if you need 3D acceleration or other stuff...
If you don't you can simply enter this command line 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select from there the resolutions you want as available by pressing the spacebar, then validate with Enter. Finally, restart X with Ctrl+Alt+Backspace, and here you go.

---

### Post by diskotek on 2007-03-27
ah, i saw your post lately... (now on another computer)
i installed withthese method [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
but now my screen is black.

i restore the xorg by: sudo dpkg-reconfigure xserver-xorg (however all i do why pressing ESC) anyway i save the day after it.

than i did that dpkg -phigh etc... i think i choose wrong resoloution because i faced the problems again. i log on twice and in second time mouse works but there is nothing click (just empty desktop-bars & wallpaper)

i'll try your offer again in graphic safe mode and try another different res.

thanks


it freezes in resoloution more than 1280 x 800, however it looks ugly and uncomfortable. it can support higher resoloution normally (like when i installed ubuntu first before update)

---

### Post by diskotek on 2007-03-27
sorry for double-post. i'm wondering how can change my screen resoloution without having an error: i'm using 1024X980 (or something like that) but it looks strecthed on 17" widescreen.

i tried most of the resoloutions but there was glitches all time on screen..

when i configure them via" dpkg configuraiton -phigh xorg-conf" like adding new resoultion rates: screen freezed on next reboot. as you see when i tried to install ati-drivers on previous posts... only thing i can get is a black screen. 

anyway; at least i have screen now, thanks for helping :) but it really looks disturbing. and this is my house-mate's computer that he's very very first timer in linux and so ubuntu; and i'm trying to get him into linux and ubuntu. seeing him using windws xp (i made it dual boot for not to cause any agression at home :D) hurts!!!

---

