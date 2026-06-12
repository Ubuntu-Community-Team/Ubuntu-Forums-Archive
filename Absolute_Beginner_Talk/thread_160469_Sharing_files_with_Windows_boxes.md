---
title: "Sharing files with Windows boxes"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by nowandever29 on 2006-04-15
OK, I admit it, I am a recovering Windows nerd.  I am soooooo new to linux, I have a question - I want to set up a media server on my network.  Not to stream files, just to offer shares that I can connect to from my Windows boxes (I have a Media Center Edition box, etc.)

So how do I go about setting up a share on an Ubuntu 5.1 box that I can connect to from Windows?  I don't mind RTFM, but I don't know where to begin...

Thanks!

---

### Post by djsroknrol on 2006-04-15
try samba...look for it in Synaptic in a search...then alter Fstab to mount your shares on the Ubuntu 'puter...then share in System>Administration>Shared folders...that easy...

---

### Post by teasum on 2006-04-15
If all you want is to set up shares, then you can set up a samba server.  A good, quick and simple how to is here, and other information can be found throughout the forums:

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

I have a simple samba server running off an old 200mHz Pentium with 160mb ram running Ubuntu and samba, and it works fine for my mp3s and backups of my work files.  Good luck!

---

