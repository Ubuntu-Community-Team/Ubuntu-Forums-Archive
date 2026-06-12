---
title: "mp3's, cd's and dvd's and codecs......"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-24
morning all
ok some advice please on a good dvd ripper and burner (preferably with a gui) i think there used to be a version of dvd shrink for linux, cant remember though.
as for cd's and mp3's ive found some programs already installed so ill give them ago first.
the other thing is codecs, now theres a multimedia sticky at the top of the page that tells you how to add the gstreamer stuff and it also has a guide for installing the win32 codecs, but i can only get as far as adding the repo's in the the sources list, it wont let me save them, so is there something im doing wrong ? (probably :D ) ive just followed the guide and copied the section that needs to be added to the sources list.
one last thing, this may sound silly, but i presume that if i just plug in my mp3 player it will be detected as a removable drive or similar, so then i can just drag n drop the files in ? its not an ipod (wont buy one because they are pants (imo) its just a cheap as chips mp3 player)
cheers.

---

### Post by Kobalt on 2007-05-24
Hello,

About your DVD thing, I'd suggest the happy couple [K9Copy]("https://help.ubuntu.com/community/K9Copy")+K3b. Use Synaptic to install them easily.
To edit the sources.list file you need the root privileges. You can do it this way : Press Alt+F2 and enter ```
gksu gedit /etc/apt/sources.list
```Give your password and after this you'll be able to edit and save the file.
Your MP3 player should be, if it's a rather simple one, be detected as a USB storage device, so drag'n'drop will be very easy.

---

### Post by techno-mole on 2007-05-24
cheers for the help, much appreciated
:D

---

### Post by stchman on 2007-05-25
> **techno-mole said:**
> morning all
ok some advice please on a good dvd ripper and burner (preferably with a gui) i think there used to be a version of dvd shrink for linux, cant remember though.
as for cd's and mp3's ive found some programs already installed so ill give them ago first.
the other thing is codecs, now theres a multimedia sticky at the top of the page that tells you how to add the gstreamer stuff and it also has a guide for installing the win32 codecs, but i can only get as far as adding the repo's in the the sources list, it wont let me save them, so is there something im doing wrong ? (probably :D ) ive just followed the guide and copied the section that needs to be added to the sources list.
one last thing, this may sound silly, but i presume that if i just plug in my mp3 player it will be detected as a removable drive or similar, so then i can just drag n drop the files in ? its not an ipod (wont buy one because they are pants (imo) its just a cheap as chips mp3 player)
cheers.

I have some resources dedicated to CD and DVD ripping, burning, MP3, etc.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

They will allow you to do pretty much what you want.

---

### Post by theicyj on 2007-05-25
And the easy method: [Automatix]("http://www.getautomatix.com/") :D

---

### Post by techno-mole on 2007-05-25
i tend not to use automatix now, for some reason i had alot of trouble with it, so now i just install from apt-get or synaptic.
cheers though.

---

