---
title: "Music player with play-speed feature? (Ubuntu)"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by EagleScout on 2008-01-18
Hey, I've been looking for a music player that is able to play songs at faster speeds. Right now I use Amarok, which would be perfect except for that one feature.

Are there any media players compatible with Ubuntu that have this feature? Or is there a way to force Amarok to do it?

Thanks!




(the reason for wanting this feature is that I'm a freshmen in college and study by listening to recordings of lectures, After hearing them in class though, I can listen to them at 3x or 4x speed and still catch everything. Its an extremely efficient study method for audio-learners - like me ^_^)

---

### Post by jeffus_il on 2008-01-18
There may be lots of options, mplayer from the command line will increase the speed by 10% each time you press ]  and vice versa with [
try ```
man mplayer
```

---

### Post by EagleScout on 2008-01-18
> **jeffus_il said:**
> There may be lots of options, mplayer from the command line will increase the speed by 10% each time you press ]  and vice versa with [
try ```
man mplayer
```


I don't think it worked... I haven't used the terminal much at all, heres what it says:

kevin@kevin-laptop:~$ man mplayer
No manual entry for mplayer

---

### Post by LowSky on 2008-01-18
how to install mplayer
```
 sudo apt-get install mplayer 
```


also try VLC it can play nearly any media

```
 sudo apt-get install vlc
```

---

### Post by NilsE on 2008-01-18
man mplayer will not work if mplayer is not installed.


mplayer with the gui frontend smplayer provides a menu option for speed control. Actually, I think the mplayer gui does also but the smplayer frontend is so much better.

smplayer is not installed by default with mplayer.  They are seperate installs but both are in Synaptic repositories.

---

### Post by EagleScout on 2008-01-18
> **LowSky said:**
> how to install mplayer
```
 sudo apt-get install mplayer 
```


also try VLC it can play nearly any media

```
 sudo apt-get install vlc
```

Thanks!! it works now! :D

is there a way to make the pitch stay the same when it plays faster? XD it is hilarious, though, to hear my prof talk like a chipmunk LOL!!

---

### Post by NilsE on 2008-01-18
> **EagleScout said:**
> Thanks!! it works now! :D

is there a way to make the pitch stay the same when it plays faster? XD it is hilarious, though, to hear my prof talk like a chipmunk LOL!!
That is also an option in command line mplayer and smplayer gui frontend.

---

### Post by alwiap on 2008-01-18
> **EagleScout said:**
> Thanks!! it works now! :D

is there a way to make the pitch stay the same when it plays faster? XD it is hilarious, though, to hear my prof talk like a chipmunk LOL!!

you can use a program called 'transcribe', ([http://www.seventhstring.com/xscribe/download.html](http://www.seventhstring.com/xscribe/download.html)), which is used for music etc., so you can write down something by ear by slowing or speeding up the pace of whatever you're listening to.  It doesn't affect the pitch at all when slowing down, I think it wouldn't if you sped it up either.

---

### Post by zakirs on 2008-01-18
by the way nice method of studying :)

---

### Post by rvm4000 on 2008-01-18
> **EagleScout said:**
> is there a way to make the pitch stay the same when it plays faster? XD it is hilarious, though, to hear my prof talk like a chipmunk LOL!!

With mplayer you can use the scaletempo filter:
```

mplayer -af scaletempo file

```

But you need a mplayer from svn (1.0rc2 is not enough).

Also smplayer has an option for it in preferences.

---

### Post by nikoPSK on 2008-01-18
there is also audacity. :)

---

### Post by EagleScout on 2008-01-19
> **rvm4000 said:**
> With mplayer you can use the scaletempo filter:
```

mplayer -af scaletempo file

```

But you need a mplayer from svn (1.0rc2 is not enough).

Also smplayer has an option for it in preferences.

it didn't seem to  like that code...here's what it said:

kevin@kevin-laptop:~$ mplayer -af scaletempo file
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.
File not found: 'file'
Failed to open file.


Exiting... (End of file)



I'm very new to Linux and Ubuntu and really don't know how the terminal commands work. (is there a good reference site for the terminal?)

I couldn't find the option in the preferences either... there is an audio filter but it asks for me to type something, it offers "resample=44100:0:0,volnorm" as an example but I have no idea what that means or what to do to change it so that it applies to pitch.

---

### Post by trash on 2008-01-19
> **NilsE said:**
> That is also an option in command line mplayer and smplayer gui frontend.

Oh thanks for the heads up on smplayer! there are some songs that sound and feel so much better when they are slowed down a tad!

smplayer even look nicer than mplayer!

---

### Post by rvm4000 on 2008-01-19
> **EagleScout said:**
> it didn't seem to  like that code...here's what it said:

kevin@kevin-laptop:~$ mplayer -af scaletempo file
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.
File not found: 'file'
Failed to open file.


Exiting... (End of file)

Instead of "file" you should type the actual filename you want to play.

Anyway, the version of mplayer you're using is old (it's more than a year ago) and it doesn't have the scaletempo filter. That filter was added to mplayer a couple of months ago.

> **EagleScout said:**
> I couldn't find the option in the preferences either... there is an audio filter but it asks for me to type something, it offers "resample=44100:0:0,volnorm" as an example but I have no idea what that means or what to do to change it so that it applies to pitch.

You also need a newer version of smplayer. You can get a deb package [here](http://smplayer.wiki.sourceforge.net/Unstable+releases). But as said before you need a recent mplayer, I don't know if there's a deb package available somewhere.

---

