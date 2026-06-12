---
title: "No sound in snes9x (using snes9express)."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by 2017-Z on 2007-12-29
I am not hearing anything from snes9express or gsnes9x.

Here's what happens in the terminal when it runs a rom
```
snes9x /home/seb/Roms/terranigma.smc
Reading config file /etc/snes9x/snes9x.conf
/dev/dsp: Device or resource busy
joystick: No joystick found.
Can't open "/dev/mem", full screen mode not available: Permission denied
```

Does anybody know how to get the sound working at all? I did a look-see about the forums and a Google but came up with nothing.

Thank you.

EDIT: Never mind it's all working after a restart. Think it was some Java based game or other. Not sure but yeah.

---

### Post by kd7swh on 2007-12-31
I use zsnes, it runs better in my opinion. But I would suggest that you compile it from source if your going to use it. The copy in the repos. is bugged.

Here is a tarball:
[http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2](http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2)

---

### Post by jonthysell on 2008-03-05
To get rid of that nasty sound error in snes9x (/dev/dsp):

Make sure you have alsa-oss and oss-compat installed:

```
sudo apt-get update
sudo apt-get install alsa-oss oss-compat
```

You then need to run snes9x with the aoss wrapper program.If you're using snes9express:

Right click on your Applications Menu and choose "Edit Menus"

Navigate to snes9express, double click, then change the command from:

```
snes9express
```

to:

```
aoss snes9express
```

I've got snes9x running fine under amd64 ... cause no zsnes ;(

---

### Post by oreo_masta on 2008-05-04
> **jonthysell said:**
> To get rid of that nasty sound error in snes9x (/dev/dsp):

Make sure you have alsa-oss and oss-compat installed:

```
sudo apt-get update
sudo apt-get install alsa-oss oss-compat
```

You then need to run snes9x with the aoss wrapper program.If you're using snes9express:

Right click on your Applications Menu and choose "Edit Menus"

Navigate to snes9express, double click, then change the command from:

```
snes9express
```

to:

```
aoss snes9express
```

I've got snes9x running fine under amd64 ... cause no zsnes ;(
Thanks, jonthysell, your note was the fix for me. I was having a similar issue after 1) switching sound cards 2) upgrading to hardy heron... I don't know what which was to blame for my sound to suddenly stop working.

Also, a note, after following your instructions they didn't work right off the bat. I had to restart kdm in kubuntu for the fix to take effect. I don't know if this was a glitch on my system or what. It's just the first thing I tried when it wasn't working initially.

Cheers!

---

