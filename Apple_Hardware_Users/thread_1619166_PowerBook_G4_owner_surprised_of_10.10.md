---
title: "PowerBook G4 owner surprised of 10.10"
date: 2010-11-11
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2010-11-11
Been trying to use Ubuntu on my PowerBook G4 for a while, and I had always found myself going back to Mac.  PowerPC owners get the short end of the stick usually, when it comes to Ubuntu.  I felt like installing 10.10 yesturday, and I was surprised of the results.  Ubuntu is actually working nearly perfect on my PowerBook.

[COLOR="SeaGreen"][B]The Good
[/B][/COLOR]
#1  Networking was working perfectly as soon as the installation was done.  Wifi was always a pain to get working in the past.  My HP printer installed without a problem, and even my Windows shares were accessible from the start as well. 

#2  Power saving features work.  In the past, the CPU ran at full speed even if you weren't using it.  Laptop got so hot, and the battery was dead in less then an hour.  Suspend would crash the laptop, unless I did it manually.  It all works fine now.

#3  Flash video is actually somewhat working.  YouTube actually works with swfdec.  Most flash animations from [www.newgrounds.com](www.newgrounds.com) seem to work, but get out of sync.

**[COLOR="Red"]The Bad[/COLOR]**

#1  The battery isn't detected.  Did the same old trick of putting pmu_battery in /etc/modules.  The battery meter shows up, but it might as well be doing nothing.  Always shows full and plugged in, when I unplug the charger. Not a new problem, just an old one that hasn't been fixed. 

#2  OpenGL hardware acceleration doesn't work from the start.  I had edit the xorg.conf to get 3D working again.  Luckily, I still remembered where to get that info [from here](http://ubuntuforums.org/showthread.php?t=1460926&page=2).

#3  Flash isn't always smooth and problem free.  YouTube videos are mostly ok, but they stutter alot.  Not a big problem, as YouTube videos stuttered in Mac OS X as well, it just stutters differently now.  Flash animations get out of sync, and you can forget flash games.  I haven't tried Gnash with working opengl, but I don't know if it uses opengl to accelerate flash.  Probably doesn't.  

Overall, I think that Ubuntu 10.10 is better then Mac OS X Leopard for PowerPC owners.  I was quiet presently surprised.

---

### Post by Dukenukemx on 2010-11-11
Just wanna add another nice surprise, that 720p HD video is playable in VLC.  I choose to use Video output of X11 video output (XCB), and HD videos that weren't playable before, are now.  The videos I tested are in .wmv format, so it certainly is a shocker.  Don't know if there's a better video output to choose, but this works. The default one doesn't, and I'd imagine that having OpenGL working is needed.

VLC on Mac couldn't do this.

---

### Post by b747pete on 2010-12-07
I am trying 10.10 on Powerbook G4 Titanium 15". I can see the Ubuntu and 4 dots then the graphics go to hell.

I am trying to boot to a Live CD to then do an install.

I believe that the video in Rage, have not tried an external monitor yet.

Any clues to help on the booting?

Thanks.

Peter

---

### Post by shawnhcorey on 2010-12-07
> **b747pete said:**
> I am trying 10.10 on Powerbook G4 Titanium 15". I can see the Ubuntu and 4 dots then the graphics go to hell.

Does the screen turn a deep, speckled blue?  It could be because of over heating.  Try this:

[LIST=1]
[*]Turn the machine off.
[*]Over the key board.
[*]Fan the internals.
[*]After about a minute, boot with the keyboard still open and you still fanning.
[*]When the desktop comes up, you can close the keyboard.
[/LIST]

I also have a Powerbook G4 Titanium and this method works for me.  :)

---

