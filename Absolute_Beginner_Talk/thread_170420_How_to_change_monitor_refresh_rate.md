---
title: "How to change monitor refresh rate?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by grandiose on 2006-05-04
Hello,

I am a total ubuntu novice and in fact, have never used any OS other than Windows before today.

I have installed ubuntu 5.10 which was really easy and have gone though all the set up and update procedure with ease also.

I want to set my monitor refresh rate to 75Hz, but there is no option to do so under the preferences > screen resolution > refresh rate drop down box... There is no other option than the 60Hz the monitor is currently using...

I did see a guide about manually changing refresh rates using some other facet of ubuntu, but after reading the first few lines I realised I was way in over my head :) .

I have only been using ubuntu for about 15 minutes so far and I have to say it looks very nice and runs without any problems. All I want to do at the moment though, is change my monitor refresh rate from 60Hz to 75Hz, so if anybody can walk me though the process in baby-steps, I would really appreciate it!

Thanks!

---

### Post by Orbatos on 2006-05-04
This sort of thing unfortunately depends a lot on your system's hardware. The "manual" process of editing of your xorg.conf file to change the resolution (which I assume is the content of the tutorial you found) is similar to writing your own monitor inf description under windows.

Can you provide information about your video card and monitor?

---

### Post by grandiose on 2006-05-04
[QUOTE=Orbatos]This sort of thing unfortunately depends a lot on your system's hardware. The "manual" process of editing of your xorg.conf file to change the resolution (which I assume is the content of the tutorial you found) is similar to writing your own monitor inf description under windows.

Can you provide information about your video card and monitor?[/QUOTE]
Thanks for your reply :) .

I haven't ever written my own "monitor inf description" under windows before, because I have always had access to all the different monitor refresh rates I wanted, so it's never really been a necessity.

As to what hardware I have, I can give you some detail on the graphics, but the monitor is just a beige, generic 16" "Relisys" monitor that I don't know a great deal about. Under Windows the monitor was just given some nondescript generic name, but it did function with 75Hz @ 1024x768, so I know it can do that.

The graphics are on-board and are documented as being "Trident Blade 3D", on a Gigabyte [GA-6VEML]("http://www.giga-byte.com/Products/Motherboard/Products_Spec.aspx?ProductID=1378") motherboard with a "VIA PLE133T" chipset.

Usually, with windows, I can't get all available refresh rates and screen resolutions before installing the drivers and I would guess it is the name with ubuntu, although I don't know... The problem seems to be however, that there are no drivers for the [GA-6VEML]("http://www.giga-byte.com/Products/Motherboard/Products_Spec.aspx?ProductID=1378") motherboard and specifically for the on-board graphics that will work with ubuntu... All the drivers on the Gigabyte web site are for Windows only, no kind of Linux support at all... I'm not quite sure what to do..?

---

