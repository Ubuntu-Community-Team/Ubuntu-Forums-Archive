---
title: "I can't change Fluxbuntu default wallpaper"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by _prophet on 2007-10-31
Can anyone tell me how to get rid of the default wallpaper on my new Fluxbuntu Gutsy install?

I know how to change the wallpaper but when it boots up it shows my custom wallpaper for a moment, then the default one pops over it... I'm confounded!

Any tips would be appreciated

---

### Post by nest on 2007-10-31
```
sudo apt-get install esetroot
```

then

```
fbsetbg -f /user/wallpaper.jpg
```

-f is for Fullscreen.

if you want more details do:

```
fbsetbg -h
```

if you still can't, try to run the fbsetbg from the esetroot terminal. but i think it won't be necessary.

oh, and don't forget to [google]("http://www.google.com.ar/search?q=how-to+set+wallpaper+fluxbox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") you question after asking.

;)

---

### Post by Greg2 on 2007-11-01
> **nest said:**
> ```
fbsetbg -f /user/wallpaper.jpg
```

This will not work in the default 7.10-rc Fluxbuntu install. Fluxbuntu uses the ROX-filer to control the background image, not Fluxbox.

Simply right-click on any desktop icon and select 'Backdrop', then drag your new image into the box.

---

### Post by _prophet on 2007-11-03
thanks so much

---

### Post by Kossilar on 2008-02-06
> Simply right-click on any desktop icon and select 'Backdrop', then drag your new image into the box.

What if you don't use desktop icons?

EDIT: Apparently you can just drag any file onto the desktop and then use that to call up the backdrop thing. Seems like a terribly long winded approach to setting the BG compared to say, right clicking on the image and then on 'Set as Desktop Background'. But apparently the Fluxbuntu filemanager doesn't include such an obvious feature :?

---

### Post by SumyTheSlayer on 2008-06-13
i have installed fluxbuntu 7.10 and... i have tried in many ways to change the background but it does not work...

i saw that if i have transparency set to the toolbar(taskbar) or to windows i can "see" underneath part of the image. but on the desktop it is the default fluxbuntu wallpaper... what could be wrong? i have also tried with startup script... and still the same problem (between the login and the time that the desktop appears i can see for a few secconds the wallpaper i have seted)

---

### Post by snowpine on 2008-06-13
> **Greg2 said:**
> This will not work in the default 7.10-rc Fluxbuntu install. Fluxbuntu uses the ROX-filer to control the background image, not Fluxbox.

Simply right-click on any desktop icon and select 'Backdrop', then drag your new image into the box.

Greg2 is correct. If you are using **Fluxbuntu**, right-click on one of the Rox icons (Home, Console, Editor, etc) and choose Backdrop. If you are using **Fluxbox**, you can use fbsetbg. 

If you are using Fluxbuntu but prefer the Fluxbox way of doing things, I'd imagine you can tell Rox not to set a backdrop (never tried it myself though).

---

### Post by SumyTheSlayer on 2008-06-13
nice... i solved the problem... i have disabled the pinboard by changing this line:
```
rox --pinboard=DEFAULT &
```
from ~/.fluxbox/startup to:
```
#rox --pinboard=DEFAULT &
```

and i used this [http://community.fluxbuntu.org/index.php?&topic=41.0]("http://community.fluxbuntu.org/index.php?&topic=41.0") to change the wallpaper...

---

