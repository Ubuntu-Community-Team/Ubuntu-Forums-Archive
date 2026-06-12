---
title: "Why are the gnome screensaver preferences missing options?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by n00bWillingToLearn on 2006-06-16
I have run other liveCD's using Gnome before and they all had options in the screensaver preferences like preview and more settings for each of the screensavers. But in Ubuntu it deosn't even let you preview so I have to wait for one minute for the screensaver to start. Recently I was trying to find the screen saver preferences in the terminal and I found two commands(why are there two commands for doing the same thing?), one gave me the same window I normally see from System-> preferences-> screensaver

```
  gnome-screensaver-preferences
``` 
And the other gave me all the features I wanted

```
  xscreensaver-command -prefs 
``` 
The problem is that even though I can see the preferenses from the second command Ubuntu still uses the settings from  gnome-screensaver-preferences
instead.

I basically want the extra features to actually work and be able to get to them without using the terminal.

---

### Post by 23meg on 2006-06-16
You can replace gnome-screensaver with xscreensaver; see [this guide]("http://ubuntuforums.org/showthread.php?t=195557").

---

### Post by n00bWillingToLearn on 2006-06-16
> **23meg]You can replace gnome-screensaver with xscreensaver said:**
> this guide[/URL]. 
Wow, great timing, I have been  searching the forums since flight 5 and when I finnally get fed up and ask a question I find someone made a howto three days before;). But thanks for the howto, I was hoping there was a way to get get the extra features back in the gnome-screensaver (I thought it was an Ubuntu thing not a Gnome thing). The drawbacks you mentioned are the same problems I was hoping could be solved by doing thing the "correct" way as I thought my solution was just a hack and thier was a better way. Oh whell I guess that is the way it goes. Still your post adds extra things like actually disabling the gnome-screensaver and changing the menu that make this much more bareable. Anyways thanks for the howto and the quick response:D

---

### Post by 23meg on 2006-06-16
Good to know you find it useful; I'm still looking for a better and prettier solution than going back to xscreensaver myself. I'll post it on the thread if I figure something out.

---

### Post by killernurd on 2006-06-18
Personally, I'm happy with where gnome-screensaver looks to be going, but I'm still going to use xscreensaver until the devs add the extra stuff that xscreensaver has to gnome-screensaver.

I want control over my screensaver, dangit! :P

And your HOWTO was a wonderful windfall - thank you! :D

---

### Post by boakes on 2006-06-21
***Warning***  

The HowTo 23meg posted would disable my wireless card after about 15mins.  It seemed to go into a perpetual state of sleep mode and, the only way to recover was to reboot.  Proceed at your own risk.

Dell e1705, w/ broadcom 4311 wlan.

---

### Post by 23meg on 2006-06-24
[QUOTE=boakes]***Warning***  

The HowTo 23meg posted would disable my wireless card after about 15mins.  It seemed to go into a perpetual state of sleep mode and, the only way to recover was to reboot.  Proceed at your own risk.

Dell e1705, w/ broadcom 4311 wlan.[/QUOTE]
Did you disable xscreensaver's power management options as I stressed in the guide? If you didn't that's probably where the problem lies.

---

### Post by enopepsoo on 2006-06-24
23meg that rules!  Way to kick ***!  My screen savers were really starting to bother me.](*,)

---

### Post by raptros-v76 on 2006-06-24
hmm, yeah. there is supposedly a way to mess with the screensaver preferences from /usr/share/gnome-screensaver/themes (or something like that) but i tried that with sonar, and it didnt work. 23megs way is probably more useful

---

### Post by 23meg on 2006-06-24
I'm happy that it helped you, but I've since posted a guide that describes a better (according to me) way of adjusting screensaver preferences without replacing gnome-screensaver. Sorry for being late to post it to this thread; [here]("http://www.ubuntuforums.org/showthread.php?t=198809") it is. > there is supposedly a way to mess with the screensaver preferences from /usr/share/gnome-screensaver/themesThat's the way I went in the new guide.

---

### Post by raptros-v76 on 2006-06-24
yeah... its not a better way. you then need to learn the whole thing of how each screensaver works, and its a mess. editing .desktop files is not fun

---

### Post by 23meg on 2006-06-24
People who don't play with the settings much may prefer it to the other method since it does the job without breaking anything and keeps the Ubuntu defaults.

---

### Post by raptros-v76 on 2006-06-24
yeah i guess. i couldnt set up the sonar screensaver properly ( i wanted it to ping a certain subnet, and it wouldnt work)

---

