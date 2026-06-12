---
title: "Screen saver fade out takes 5 minutes and I can't use the computer"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by manuelrazzari on 2006-07-09
When the screen saver activates, it fades out, and it takes about 5 minutes before it finishes fading out. In that 5 minutes, I can't interrput it. So I have to wait until it's done fading and the screen saver starts, to be able to get back to work.

How do I disable fading, or how do I get to be able to interrput it?

I'm on a Powerbook G4 titanium 550 running Ubuntu 6.06 Desktop. 

Thanks for any help.

---

### Post by macgig on 2006-07-12
strange, fade out is quick on my old g4 tower. I dont see any option to disable it under: system>preferences>screensaver

unless ive missed it. ? :confused: 


> **manuelrazzari said:**
> When the screen saver activates, it fades out, and it takes about 5 minutes before it finishes fading out. In that 5 minutes, I can't interrput it. So I have to wait until it's done fading and the screen saver starts, to be able to get back to work.

How do I disable fading, or how do I get to be able to interrput it?

I'm on a Powerbook G4 titanium 550 running Ubuntu 6.06 Desktop. 

Thanks for any help.

---

### Post by desmondo on 2006-10-07
I had the same problem with a ThinkPad T40.  Using this [thread]("http://www.ubuntuforums.org/showthread.php?t=198809"), I was able to turn off the fading.

1.  Install xscreensaver.
```
sudo apt-get install xscreensaver
```

2.  Launch the xscreensaver configuration
```
xscreensaver-demo
```
As mentioned in the referenced thread, > when asked whether you want to launch the daemon, **[COLOR="Red"]click "Cancel". This is important[/COLOR]**, since running both the xscreensaver and gnome-screensaver daemons together is very likely to cause unwanted behavior.

3.  On the advanced tab, uncheck the box next to fade, then quit.

I'm not sure if rebooting is necessary, but I did it.

---

