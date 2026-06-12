---
title: "lines flickering on my screen"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by crazy_wookie on 2006-07-09
hello!
i tried ubuntu from a live cd and i like it.. i want to install it to my hdd but when i ran it from live cd i got little horizontal line flickering on my screen
 that happened in 1280 x 1024 screen res.. and this is the resolution i like to use (when i switched to 1024 x 768 the lines dissapeared)
 so.. question.. if i install ubuntu on my hdd will those lines continue to flicker on my screen? if yes how do i fix this?
    thank you very much,

---

### Post by woedend on 2006-07-09
do you suppose its refresh related...when you set it to 1280 x 1024 what is your refresh rate?

---

### Post by crazy_wookie on 2006-07-09
it's 60 hz.. and i am sure my monitor can handle this refresh rate.. anyway.. i cannot change the refresh rate.. it is automatically set at 60

---

### Post by cyberlite on 2006-07-09
What kind of video card do you have & monitor ?

---

### Post by crazy_wookie on 2006-07-09
videocard geforce mx440 with agp8x
monitor hyundai image quest v773

---

### Post by cyberlite on 2006-07-09
in the monitor screen right under there is box witch is selected, unselected, then you can then freely selected a refresh rate.But be worned look at the propertis of the screen. and I think you set.

---

### Post by RaZer0r on 2006-07-09
when ubuntu is installed just use this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
to install your n-vidia drivers, I have the same graphics card and didn't have any problems at all.
If the problem still wouldn't be fixed try
```
 sudo dpkg-reconfigure xserver-xorg 
```
and use expert options (make sure you got the tech information about your monitor)

---

