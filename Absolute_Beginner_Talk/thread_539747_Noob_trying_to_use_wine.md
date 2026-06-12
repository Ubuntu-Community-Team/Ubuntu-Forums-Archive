---
title: "Noob trying to use wine"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by be_direct2002 on 2007-08-31
hi um im brand new to linux , and im useing ubuntu,, im trying to instal a few different programs, one being WInamp ,,just becuase i like winamp,, but it tells me i dont have arial.ttf instaled, i went and downloaded the Microsoft Core fonts,, i dont know whats wrong or how to fix it ,, can someone help me please.. thank you

---

### Post by ericmitz on 2007-08-31
> **be_direct2002 said:**
> hi um im brand new to linux , and im useing ubuntu,, im trying to instal a few different programs, one being WInamp ,,just becuase i like winamp,, but it tells me i dont have arial.ttf instaled, i went and downloaded the Microsoft Core fonts,, i dont know whats wrong or how to fix it ,, can someone help me please.. thank you

Maybe you have to install arial within wine, and not in Ubuntu? try putting arial.ttf in the folder:
```

/home/user/.wine/drive_c/windows/fonts

```


You could always switch to XMMS :guitar:

---

### Post by familyjules74123 on 2007-08-31
welcome to ubuntu!  first and foremost, have you checked out the media players that the synaptics package manager has to offer?  I raise this because wine tends to get kinks and glitches in it and I wouldn't suggest using it for a media player.  You might want to look into a website that will tell you much about what each of the media players offers such as: 

[http://ubuntu-tutorials.com/2007/01/29/media-players-for-gnome-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/29/media-players-for-gnome-ubuntu-6061-610/)

something like that can be very helpful to you to make a decision.  If these players don't fill your needs, then please come back to the thread and let me know.

---

### Post by sumguy231 on 2007-08-31
This doesn't exactly solve your problem, but I think you'd be better off running one of the many native Winamp clones such as xmms, beep media player, or audacious. Or check out a good non-Winamp clone like Amarok or Rhythmbox.

---

### Post by be_direct2002 on 2007-08-31
[SIZE="5"]thanks for all the suggestions,, I have looked at xmms, i couldn't find a feature on it that does the same thing as win amps media library window,,, that could just be because i am unfamiliar with it,, but that is my main and biggest reason for wanting to use win amp,,, i love the media library window ... ,,, also im not quite sure how to copy the font in to the wine c/windows/font's directory,,, i have tried what i would think is the way to do it but it doesn't do it,, again unfamiliar.. any suggestions would be awesome.. thanks again 
[/SIZE][/SIZE]

---

### Post by sumguy231 on 2007-09-01
If you have msttcore-fonts installed, do this:
```
cp /usr/share/fonts/truetype/msttcorefonts/arial.ttf ~/.wine/drive_c/windows/fonts
```
That will copy the font over.

Do this to list the fonts:
```
ls ~/.wine/drive_c/windows/fonts
```


I must warn you though, I have used Winamp in Wine before and I didn't have that smooth an experience. Amarok takes a similar approach to its user interface, so you might still look into that.

---

