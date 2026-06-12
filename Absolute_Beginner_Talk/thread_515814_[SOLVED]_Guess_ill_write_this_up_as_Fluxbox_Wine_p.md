---
title: "[SOLVED] Guess ill write this up as Fluxbox Wine problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-08-02
Not sure where to begin on this one. I've been running fluxbox for a while, got everythign set up... also running eterm since it was easiest to do what i wanted it to... well...

Last nite i stumble upon Tales of Pirates and im like rock, sounds fun... so off to install wine i go... Then i get to winecfg and the problems start... got a couple.

First... when i run anything via wine it reloads my desktop (you fluxbox users know what im talking about) wich isnt a problem except then i have like 2 of every app running on my desktop (the second ones consuming about 5x the resources they should). This happend when i ran winecfg and when i ran wine top.exe. Any clue as to why wine is telling fluxbox to reload everytim its utilized.

Second and main problem is, Wine is displaying garbage for characters. I think this might possibly have to do with the export LANG=C that i had to add to my .profile and .bashrc to get midnight commander to display right. then again it might not... ill attatch a screenshot so you can see what i mean by garbage for characters. I had this problem in winecfg (wich i was good enough to navigate around without text) and when i run top so i cant play because i cant figure out wich button to push... and now for the screenshot

but first, if it is a export LANG=C problem, does anyone have any luck running midnight commander inside of aterm... basically i need a terminal emulator that is easy to configure to be transparent, with no borders or titlebar or scroll bar... im sure aterm can do all this, ill just have to figure it out... but before trying i would like to find out if i even have to change...

---

### Post by Nythain on 2007-08-02
well this is turning out to be a pretty crappy day.

first i find that even aterm requires the export LANG=C workaround to correctly display teh characters in midnight commander

then i find out that removing that line has no effect on wine whatsoever.

so now im back to square one... any clue what would be causing the windows and buttons wine creates to be all jacked up???

guess on the brightside i dont have to delve into configuring a new terminal... though i really want to play this game and would hate to have to go back to kde just for it

---

### Post by bodhi.zazen on 2007-08-02
The problem is you need to install some true type fonts for wine.

see if this thread helps : [http://ubuntuforums.org/showthread.php?t=274052](http://ubuntuforums.org/showthread.php?t=274052)

I do not think wine tools is working with current versions of wine.

Start by installing msttcorefonts

---

### Post by Nythain on 2007-08-02
much thanks... am working on it now... gotta GET some fonts first... never had this problem before, could be because before i was running kubuntu installed from livedvd and now im running a much more minimal system (command line install with x and fluxbox added post install) so im guessing  it must be something that the livecd/dvd's install that doesnt get installed with a command line system since it really has no need for fancy pants microsoft fonts

---

### Post by Nythain on 2007-08-02
ok, one problem down... two more to go... now i gotta figure out why wine keeps wanting to reload fluxbox and then i have to research how to get this game goin in wine... back to the drawing board for me... thanks for the font help

---

