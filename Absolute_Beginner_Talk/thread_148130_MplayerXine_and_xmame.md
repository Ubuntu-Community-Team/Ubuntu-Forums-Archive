---
title: "Mplayer/Xine and xmame"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by manoman on 2006-03-21
Hello! My computer apparently doesn't like Windows anymore. After reinstalling the system three times and trying to update to SP2 I just gave up and decided to give Linux a try. I got it up and running smoothly. I'm just having problems installing programs.

The programs I want to install is a media player capable of video playback. Totem doesn't want to play anything, so I did a search and found Mplayer and Xine. Three hours later, I still can't run them. I've done the whole "./configure; make; make install" thing but I'm confused on where to go after that... or even if I did that right. I want the programs to appear in the application menu as well, but I'll at least settle for a simple icon on the desktop.

I've also tried to install xmame, which is an arcade emulator, to no avail as well. I even read a thread on here ([http://ubuntuforums.org/archive/index.php/t-86213.html](http://ubuntuforums.org/archive/index.php/t-86213.html)) where instructions were given how to install the program, but they just didn't work for me.

Not to offend anyone, but the documentation is really poor. I still haven't found a step-by-step way to install something for beginners. Everything assumes you have some knowledge before hand and have successfully installed stuff before (which is silly, because if you have why would you need to read that section of the documentation??). They especially don't tell you how to get the program running after you install it.

I hope I'm not asking too much here. Any help would be appreciated. Thank you!

---

### Post by trent dillman on 2006-03-21
Instead of compiling (which is what all that 'configure/make/make install' stuff is), you should instead try using Synaptic. 

If you use gnome, it's under system > administration > synaptic package manager. If you use something else, like kde or xfce, try opening a terminal and use ```
sudo synaptic
```

You also need to have some extra sources in your /etc/apt/sources.list
Installing [Automatix]("http://ubuntuforums.org/showthread.php?t=138405") should do the trick.

---

### Post by Princey on 2006-03-21
[QUOTE=trent dillman]Instead of compiling (which is what all that 'configure/make/make install' stuff is), you should instead try using Synaptic. 

If you use gnome, it's under system > administration > synaptic package manager. If you use something else, like kde or xfce, try opening a terminal and use ```
sudo synaptic
```

You also need to have some extra sources in your /etc/apt/sources.list
Installing [Automatix]("http://ubuntuforums.org/showthread.php?t=138405") should do the trick.[/QUOTE]

Automatix also takes care of the win32 codecs stuff that he's fighting about if he choses to install mplayer. I'd advise him to check automatix out. Will save him a few hours of work at the terminal, I'm sure.

---

### Post by trent dillman on 2006-03-21
It also enables every apt source that anyone using *ubuntu as a desktop could need.
:-D

---

### Post by manoman on 2006-03-22
Wow thanks! That Automatix has a ton of stuff! It got mplayer up and running as well. I couldn't find out how to install xmame through Synaptic, so I went to debian.org and using the dpkg stuff I somehow got xmame to work now, so that's cool.

I do have one little problem though. Apparently I installed something bad in Automatix because my CD rom drive isn't working anymore. I insert the cd and it appears on my desktop, but when I open it up there's nothing inside. This kind of sucks seeing as my paper is on a cd and I need it fast. :-? Any help? Thanks again.

---

### Post by Sandlst on 2006-03-22
Ive had this problem many times; the only fix I've found is manually ejecting the cd ```
eject
``` then re-entering it.  Hope this works for you!

---

### Post by manoman on 2006-03-22
Hey that worked. Heh.

Now I see what the problem was. Linux doesn't want you manually ejecting the cds... and I installed the "manually eject cd" option in Automatix. Thanks!

---

