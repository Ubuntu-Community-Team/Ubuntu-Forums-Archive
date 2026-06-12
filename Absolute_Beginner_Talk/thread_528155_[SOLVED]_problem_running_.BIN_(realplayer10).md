---
title: "[SOLVED] problem running .BIN (realplayer10)"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2007-08-17
(brand new to linux)

I'm trying to install RealPlayer to play my .SMIL files...
unfortunately i can't seem to find it in the repositories and needed to download a .bin file.

I have absolutely no experience with .bin files.

if i open the icon, it asks me what program to run it with...no clue

if i try ```
./RealPlayer10GOLD.bin
```

I get an error saying either command not found or no such directory.

if i try: ```
chmod +x RealPlayer10GOLD.bin

./RealPlayer10GOLD.bin
```

i get: ```
./RealPlayer10GOLD.bin: error while loading shared libraries:
libstdc++.so.5: cannot open shared object file: No such file or directory
```

i'm stuck, help please?

many thanks,

---

### Post by riven0 on 2007-08-17
I'm not too good at BIN files, but did you try putting sudo in front of the command?


First:
> 
sudo chmod +x RealPlayer10GOLD.bin

Then:

> sudo ./RealPlayer10GOLD.bin

---

### Post by tango_ninja on 2007-08-17
well I tried it, but same get the problem with the libraries as above post...

---

### Post by gobbles414 on 2007-08-17
It is very easy to play real player Real files without Real Player. On my system, I use a combination of Gstreamer, W32codecs, and the MPlayer plugin for Firefox. *EDIT: I also have Ubuntu Restricted Extras installed. All of these are available in the Synaptic package manager if you follow the directions listed [here]("https://help.ubuntu.com/community/RestrictedFormats").*

---

### Post by Seisen on 2007-08-17
You can install helix player  and the mozilla-helix-player plugin from the Universe repositories,

---

### Post by tango_ninja on 2007-08-17
i actually tried Helix, because I heard it can also play many realplayer files

installed it about 10 min ago and when i try to open this .SMIL file it pops an error message to me effectively saying <helix cannot open this file. get reaplayer>

---

### Post by tango_ninja on 2007-08-17
here's working solution.

Open Adept Manager, and add a new 3rd party repository
(deb [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) stable main)

realplayer10 can be found in this repod (debian)

---

### Post by Perfect Storm on 2007-08-17
[http://www.filefactory.com/file/c0d8bd](http://www.filefactory.com/file/c0d8bd)
I have uploaded a .deb of Realplayer 10, the .deb package is in .tar.gz

---

### Post by igknighted on 2007-08-17
Don't use debian repos!!!!

Use this one, it is canonical's commercial software repo (has realplayer, opera and a few others):

```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

---

### Post by tango_ninja on 2007-08-17
ok i'm changing....what's wrong with the debian one?

---

