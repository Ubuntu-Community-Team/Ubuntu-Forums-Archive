---
title: "Ubuntu on Dell Inspiron 1720"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by cadcrazy on 2008-01-31
Just purchased Dell Inspiron 1720 with following config

C2D 2.00 GHz
2GB RAM
250GB HDD
GeForce 8600m GT
1440 X 900 screen resolution

It come preloaded with vista.Booted from live cd and installed Ubuntu 7.10. I have few problems.

- Sound is not working.Sound card is intel azila or something similar
- After i installed latest nvidia driver from their website i am not able to see top window bar for any application ( the bar with close,minimize,restore window buttons). See the attached image

[[IMG]http://img209.imageshack.us/img209/9651/screenshotmf8.th.png[/IMG]](http://img209.imageshack.us/my.php?image=screenshotmf8.png)

Plz help me solve these problems

---

### Post by oedha on 2008-01-31
did you install compiz ???
because it happen to me when i messed with windows decoration of compiz

~E~

---

### Post by oedha on 2008-01-31
i am sorry....too many posts....i have connection problem just now
~E~

---

### Post by cadcrazy on 2008-01-31
did you mean compiz-configsettingsmanager package. No 
Just installed os followed by nvidia driver and nothing else

---

### Post by mevets on 2008-01-31
Yeah it seems like compiz is failing. Open a terminal and run:
```

gtk-window-decorator

```
Does that work?

---

### Post by cadcrazy on 2008-01-31
compiz is not enabled yet. Everything was fine before nvidia driver.

---

### Post by oedha on 2008-01-31
compiz will install by default by gutsy gibbons
have you done like mevets #5 suggested ?
or 
right click on your desktop.....change desktop background
go to visual effect....make it none

~E~

---

### Post by Takuhari on 2008-01-31
I hate the vista home edition!!! it freezrs up on me,,,

If you uninstall it, and reinstall either vista vistapro xp xppro... there will bee a bluetooth problem...

you will need to use the bluetooth turnon switch>_<

It took me forever to get it form dell... bad CS>_<

if you want it... send me a pm with your email... and i will email it to you...
This goes for all the dells with bluetooth turnon problems...

---

### Post by peakshysteria on 2008-01-31
Open up a terminal and write: alsamixer for fixing your sound problems. There you can see if there is something which is not enabled. Use the arrow keys to higher or lower the values.

And yeah. Try to enable Compiz to solve your window problems. And maybe install Compiz settings manager from synaptic and play with the settings to see if there is something wich can make things right.

---

### Post by skymera on 2008-01-31
install the nVidia driver through envy.

works flawless all the time.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cadcrazy on 2008-01-31
After setting the visual effects to none everything is back to normal. But how can i enable compiz on my lappy. Also here is the output of the gtk-window-decorator after setting effects to none

```
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
```

---

### Post by cadcrazy on 2008-01-31
Output of alsamixer
```
alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by mevets on 2008-01-31
You have to run
```

gtk-window-decorator --replace

```
But it sounds like once you turn off compiz that you get window decorations back, so I dont know that you really need that.

Once you get compiz working properly you mostly likley wont have the decoration problem. iIt would probably be best if you ninstaledthe nvida driver you installed and install it again thru envy as someone earlier suggested.

---

### Post by cadcrazy on 2008-01-31
whats the prob with manual install as i have successfully installed it before on many computers.

---

### Post by Alx c on 2008-01-31
This isnt exactly about this but try compiz-fusion (berly+compiz) its good.

---

### Post by cadcrazy on 2008-01-31
??

---

### Post by cadcrazy on 2008-02-01
bump

---

### Post by cadcrazy on 2008-02-02
Anybody plz help me get sound and compiz working on my lappy

---

### Post by cadcrazy on 2008-02-02
Where are the all ubuntu geeks

---

### Post by cadcrazy on 2008-02-02
i wonder why no one is helping me

---

### Post by cadcrazy on 2008-02-03
bump

---

