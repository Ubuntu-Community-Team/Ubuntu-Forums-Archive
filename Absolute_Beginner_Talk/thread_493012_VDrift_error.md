---
title: "VDrift error"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-05
i was flicking through synaptics the other day and came axcross a game called VDfrit.
itwasnt the best game in thwe world, but would be nice to play it again

however when iwas playin it jus suddenyl shut down and now dosent boot up.

you have to put 
```
 vdrift 
```

in the terminal, this is the result.

```
 
scott@scott-desktop:~$ vdrift
BinReloc successfully initialized.
Executable path: /usr/share/games/vdrift/bin/vdrift
Data dir: /usr/share/games/vdrift/data
Localedir: /usr/share/games/vdrift/share/locale
No data_dir found in VDrift.config, using /usr/share/games/vdrift/data
Found config file /home/scott/.vdrift/controls.
Found config file /home/scott/.vdrift/VDrift.config.
No data_dir found in VDrift.config, using /usr/share/games/vdrift/data
Version of game: 2007-03-23
Skin name not found in config file...
Warning: option-47 is missing its default value. Assuming "".
Run with -verbose for troubleshooting.
Run with -nosound to disable sound.
Run with -benchmark to play a replay and output benchmark data.
0 joystick(s) found:
Segmentation fault (core dumped)
scott@scott-desktop:~$ 
```

---

### Post by moredhel on 2007-07-05
first try reinstalling it:

(type into terminal)

```
sudo aptitude reinstall vdrift
```

---

### Post by skymera on 2007-07-05
no luck ,the same error.

---

### Post by moredhel on 2007-07-06
try sudo aptitude purge vdrift

then reinstall. If that still is wrong then It's more likely a problem with graphics drivers or something, does the game require opengl? if so do other opengl games work?

You can test if opengl works at all by typing glxgears into terminal.

---

### Post by go_beep_yourself on 2007-12-09
Try a deb from getdeb.net or else get the source code and compile the game.

---

### Post by go_beep_yourself on 2007-12-09
Anyone else have no sound or know how to get sound in the game? I even tried running the game with aoss and had the same problem.

---

### Post by Dr Small on 2007-12-09
I use the deb from getdeb.net and it worked fine.

---

### Post by go_beep_yourself on 2007-12-11
> **Dr Small said:**
> I use the deb from getdeb.net and it worked fine.

Which deb? There's three of them. I used a deb from there as well.

---

