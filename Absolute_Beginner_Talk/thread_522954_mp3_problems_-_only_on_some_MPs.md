---
title: "mp3 problems - only on some MPs"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by crav on 2007-08-11
I'm having a problem playing back mp3s - but only on some media players. XMMS, VLC, and Rhythem Box all play mp3s. Amarok, Exaile, Kaffeine and GXine all have problems with mp3s. I've followed the guide stickied at the top of this forum. Any ideas as to what is causing only these certain programs to have mp3 issues?

---

### Post by Amros on 2007-08-11
Hey there!

I'm having the exact same problem, only here gxine won't play mp3's either.
I get the error "The xine engine failed to start" (when trying with gxine).

Any thoughts anyone?

---

### Post by Pioneer5000 on 2007-08-11
Just stick to XMMS for music and VLC for video well thats what im doing. For me amorok just wont work it just lags when i try to ply something and then just freezes. i guess i would also like help on this issue so hopefully someone will answer our call for help.

---

### Post by Pioneer5000 on 2007-08-11
Ive got Amarock working guys, what i did was tried to connect to lastFM radio thing and then a message box came up and said Amorock is not set to play mp3's do you want to enable i was like ok and then it installed some file and now it works.

---

### Post by forestpixie on 2007-08-11
you can try installing libxine-extracodecs for amarok mp3 support. 

sudo apt-get install libxine-extracodecs

there might be another one but I can't remember the name - if you install it have a see if it suggests any other packages

---

### Post by Amros on 2007-08-11
Thanks forestpixie!

It suggested the package libxine1-ffmpeg, witch I installed, and now it works like a dream :)

---

### Post by forestpixie on 2007-08-11
1 down - 2 to go :)

---

### Post by crav on 2007-08-11
```
crav@AlphaCrav:~$ sudo apt-get install libxine1-ffmpeg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Still no sound

---

### Post by Amros on 2007-08-12
Did you try to install libxine-extracodecs to see what it suggested? Perhaps it will suggest something different for you. Just a thought, I don't really know..

---

### Post by forestpixie on 2007-08-12
try doing this in terminal it will add codecs - if you have any of them it will just tell you that you've got latest version

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

---

### Post by crav on 2007-08-13
> **forestpixie said:**
> try doing this in terminal it will add codecs - if you have any of them it will just tell you that you've got latest version

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

Did this, I now have just about every codec known to man now... still doesn't work though.

---

### Post by Arthur Archnix on 2007-08-13
Is this Amarok from the ubuntu repos? If so, try downloading the feisty deb from their site. Do a sudo apt-get remove amarok before installing the downloaded deb file.

Also, one handy little command gets you most of what you need codec wise:
```
sudo apt-get install ubuntu-restricted-extras

```

I seem to recall having a similar problem with an older version of Amarok. Mine is currently running on the gxine engine, but that should be installed as a dependency when you install amarok. When you have the new version, if it doesn't work, try changing the output under engine in configure from autodetect to alsa.

---

### Post by Wynne G Oldman on 2007-08-18
> **Pioneer5000 said:**
> Ive got Amarock working guys, what i did was tried to connect to lastFM radio thing and then a message box came up and said Amorock is not set to play mp3's do you want to enable i was like ok and then it installed some file and now it works.
Nice one! I've been struggling with this for about a week. Your tip worked. Many thanks.

---

