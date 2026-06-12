---
title: "Change DVD autoplay program"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by crash331 on 2006-08-25
When I insert a DVD, Ubunto automatically brings up totem movie player.  I do not like this player and it doesn't perform as well as xine player that I have.  How can I change it so that xine will load when I insert a DVD, or to make nothing play at all.

---

### Post by orb9220 on 2006-08-25
Just right click on file like movie.avi and change from thier it will change it for all .avi files. You will have to do it for mpeg,mpg,wmf,etc for each one.

---

### Post by Sandlst on 2006-08-25
Go to System/Preferences/Removable Drives and Media, click on the multimedia tab, and change the 'Video DVD Discs' Command to xine.  Post back if you have any problems.

---

### Post by crash331 on 2006-08-25
Ok, in the preferences it did say "totem %m".  I changed this to "xine %m" but I don't think it passes the same arguments because xine was all screwey and loaded at a weird size, it played theNew Line Cinema splash screen, and then gave multiple errors about not being able to find vob files.

Any idea what arguments to pass to xine?

---

### Post by crash331 on 2006-08-25
I got it, I used xine --no-splash -D dvd://

If anything else important needs to be passed, let me know.

---

### Post by Sandlst on 2006-08-25
Ah, sorry about that.  Put in ```
xine --auto-play --auto-scan  dvd
```or ```
xine --auto-play --auto-scan  dvd -F
``` For auto-start in fullscreen.

---

### Post by crash331 on 2006-08-25
> **Sandlst said:**
> Ah, sorry about that.  Put in ```
xine --auto-play --auto-scan  dvd
```or ```
xine --auto-play --auto-scan  dvd -F
``` For auto-start in fullscreen.



Cool, I just modified that a little to hide the gui, remove the splash screen and de-interlace, or else it looks yucky.  Wound up with:

```

xine  --hide-gui --no-splash --auto-play --auto-scan  dvd -F -D
```


And I didn't even think to just type xine into the terminal to see all the arguments. I guess you can tell I come from windows...

---

