---
title: "[SOLVED] about GNOME MPlayer"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-19
i have been trying to find a movie player that will work on my computer because most media players will close out when i click play (for some strange reason).

I have just found the only movie player that i can get to work and that is GNOME MPlayer.
I have tried many media players including VLC, Totem ,and the regular MPlayer but so far only GNOME MPlayer works.
My problem is that it is not set as my default movie player.
when i click on a movie it tries to open totem and totem doesn't work so it just pops up and disapears real quick.

Is there some way that i can set GNOME MPlayer to my default for opening movies?

Also a second question is regaurding the Play,Stop, Fast Forward, and Rewind buttons on my keyboard, is there any way i can setup GNOME MPlayer and Exile to use these keyboard buttons?

---

### Post by ghanthar on 2008-02-19
>  Is there some way that i can set GNOME MPlayer to my default for opening movies?This would also affect your audio files but this is the easiest way System>Preferences>Preferred Application >Multimedia and then choose gmplayer or choose custom and type gmplayer.

> Also a second question is regaurding the Play,Stop, Fast Forward, and Rewind buttons on my keyboard, is there any way i can setup GNOME MPlayer and Exile to use these keyboard buttons?I do not use any Mplayer based app so dont know about it but for exaile you have a plugin for it. 
edit>plugins>available plugins. you should see a "Global Hotkeys" plugin there, just check it and install it. After that you must enable it from "Installed Plugins" and the gnome keyboard keys should work now.If not you should check Systems>Preferences>Keyboards Shortcuts and setup your keyboard shortcuts for Gnome.

---

### Post by r4ik on 2008-02-19
In synaptic remove Totem-Mozilla and add Mozilla-mplayer

Good luck !

If it still is a no worky please read,

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by tjwoosta on 2008-02-19
thanks 

I already have the mozilla-mplayer plugin ,all of that works fine
it is only when i try to open movies i have saved on my computer

i tried the preferred applications  but it still tries to open things with totem for some reason

i will try to just remove totem and see what happens.

---

### Post by tjwoosta on 2008-02-19
Ok after removing totem everything tries to open with the original MPlayer instead of GNOME MPlayer 
I tried to remove the original MPlayer but it says i need it for GNOME MPlayer, Mozilla-MPlayer, AcidRip, and DeVeDe.

I also right clicked the icon on my desktop and went to properties then clicked the launcher tab and used that command for the preffered applications command but that also did not work.

What can i do to make it open with GNOME MPlayer?

---

### Post by benny bronx on 2008-02-19
Save the file to your comp, then right click on it.  Go to "open with", and add the media player you want.

---

### Post by tjwoosta on 2008-02-19
that is what i have been doing but i have right click and pick open with GNOME MPlayer every time i want to watch a video , i was just hoping that i could make it default.

---

### Post by ghanthar on 2008-02-19
> I also right clicked the icon on my desktop and went to properties then clicked the launcher tab and used that command for the preffered applications command but that also did not work.Is this mean what I described below?
If not just try it it worked for me for every type of file that I tried....

** Right click to the file and select *properties *click the* open with *tab and select mplayer. This should work with this type of files...so you should repeat the process for every desired file type but at least this should solve the problem.**

---

### Post by tjwoosta on 2008-02-19
thanks ghanthar

it worked !

---

### Post by ghanthar on 2008-02-20
:) Great happy that we could solve it. What about hotkey problems?

---

### Post by tjwoosta on 2008-02-20
i got the hot keys working with exile but i still dont know how to do it with GNOME MPlayer, but thats not really a big deal to me. (as long as exile works)

---

