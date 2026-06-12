---
title: "[SOLVED] Help ati driver and reboot black screen"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by billmik on 2008-01-21
anyone have this problem? Using any player totem or others i tried the movie or video plays underneath (bottom) of the video player. Not in the section where it should play has a bluish tint sometimes also. i installed restricted ubuntu extras or gstreamer codecs and i get this problem. Any help?

Ok update
I found when i enable the ati restricted driver this happens if i disable the ati restricted driver the videos play normal again. So now i installed the new ati driver in accordance with this guide [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
and all goes well like explained.

Any every time i go for the reboot part after
Finish the Installation
Now save any open document and reboot your system:

sudo shutdown -hr now

on reboot i get the ubuntu screen with the orange loading line after that the screen goes black and the hard drive light goes out. I tried to ctrl+alt+F1 and nothing happens. All i can do is boot in recovery mode up to the prompt telling me to type something in.

Help Plz I wanna get this right so i can get rid of xp

---

### Post by zipperback on 2008-01-21
Please tell us the detailed specifications of your hardware.

Please tell us which specific distribution of Ubuntu you are working with including if it is the 32bit or 64 bit version.

Thank you
- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-21
Also, could you please provide us the output of the following command.


```

lspci

```

That will tell us a little more about your hardware too.

Thank you.

-zipperback
:popcorn:

---

### Post by billmik on 2008-01-21
ok i tried the 1shw and 1spc1 at prompt in recovery mode and nothing

Running 7.10 gutsy 32bit  ati x1300 video card 512 memory 2.8 celeron d 2gig system memory

---

### Post by spiderbatdad on 2008-01-21
that's a small "L" as in lshw "list hardware" lspci "list pci"

---

### Post by billmik on 2008-01-21
K sorry
I typed lspci and lshw and after pageing up the only thing i see that relatesto video or a problem is

01:00.0 VGA Comp controller ati tech inc rev516 (radeon x1300/x155 0 series

01:00.1 Display controller :ati tech inc rv516 (radeon x1300 pro) secondary

Does this help? or exactly what are you looking for

---

### Post by spiderbatdad on 2008-01-21
seems like there is a problem running composited environment and totem at the same time. There is a tool in synaptic for quick switching of gl. I think it's called gnome-compiz-manager. Puts itself in Preferences under the name GL Desktop.

---

### Post by billmik on 2008-01-21
Ok thanks ill try that, but i still need help with this driver install. Its a agp card does this make a difference?

---

### Post by spiderbatdad on 2008-01-21
sorry. thought you had the driver working at one point... can you boot to desktop now? If so, try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by spiderbatdad on 2008-01-21
i checked the link of your op...there is no text there.

---

### Post by spiderbatdad on 2008-01-21
if you're still stopping at boot like you described...try hitting the esc key a few times and waiting...then a few more times....if it eventually boots reconfigure xserver, then look at /etc/usplash.conf x and y may not match your supported screen resolution...edit by terminal```
gksu gedit /etc/usplash.conf
``` and save.

---

### Post by billmik on 2008-01-21
ok sorry

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Ok i did the sudo dpkg-reconfigure -phigh xserver-xorg and the 1st time it was asking me refresh rates etc and when i tried it again after selecting fglrx it didnt ask me the other screen it went back to prompt. i cant get ti to go back to the other screens lol. o well i selected fglrx and then sudostartx and the black screen again. then i reconfigured again selected vesa (again no additional screens) back to prompt then startx and it booted back to like original no refreshrate selection just like at gutsy install. I'd like to get this ati driver working really

Thanks for your help most forums people dont help but im really happy with the help on ubuntu forums you guys are great

---

### Post by spiderbatdad on 2008-01-21
this may be what you're looking for:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
though i would suggest looking through synaptic first for a driver like xorg-driver-fglrx and xorg-driver-fglrx-dev...or try the restricted driver again and remember to try the gnome gl desktop tool to turn off gl when running totem...are you trying to have advanced desktop effects? maybe all you need is xserver-xgl...reboot and select "custom" under Preferences > Appearances > Visual effects.

---

### Post by billmik on 2008-01-21
ok thanks ill try that special effects are nice, but what i really want is to change resolution and refresh rates

---

### Post by spiderbatdad on 2008-01-21
there is another tool in synaptic called displayconf-gtk  install itself under System>>Administration>>Screens and Graphics

---

### Post by billmik on 2008-01-22
Ok Spiderbatdad i got it all to work. I used the ubuntu restricted driver like you said, and the videos went underneath again like they were before. I tried the gnome-compiz-manager and it didnt help with totem.  So i tried the xserver-xgl you suggested and when i tried to select custom it had no selection, so i selected normal effects and they work, at the same time totem started playing videos the right way. Thanks for all your help i got everything now the way i wanted it

bill    :)

> **billmik said:**
> anyone have this problem? Using any player totem or others i tried the movie or video plays underneath (bottom) of the video player. Not in the section where it should play has a bluish tint sometimes also. i installed restricted ubuntu extras or gstreamer codecs and i get this problem. Any help?

Ok after digging further into this problem i solved it finally. hit alt f2 type gstreamer-properties hit run  goto the video tab,  Under default output select x window system (noXv) then close. Videos play where they are supposed to now

---

