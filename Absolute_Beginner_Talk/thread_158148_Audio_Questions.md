---
title: "Audio Questions"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Kevin_Vortex on 2006-04-10
Hiya. I'm running Dapper Drake and was wondering if anyone knew which packages I should install to be able to listen every type of audio file in XMMS especially aac...
I'm also looking for Digital DJ software with a cross fader and mix recording capabilities. Something like Virtual DJ for PC/Windows would be optimal.

And the ultimate question of life the universe and everything... Oh wait this isn't that question... Its just as important though. Are there any backports for Dapper Drake yet and if not are there any older version backports that will work?

---

### Post by Kevin_Vortex on 2006-04-11
**bump**
Can anyone help me with this?

---

### Post by cleverselfreferentialname on 2006-04-11
Install xmms-mp4 to get AAC and mp4 support, xmms-flac to get FLAC support, and xmms-mad to get mp3 support (though I thought it already had it).

You might need to enable the universe repository for some of these, so (if you have Ubuntu/GNOME) run ```
sudo gedit /etc/apt/sources.list
``` and if you have Kubuntu/KDE substitute kedit for gedit.

When your sources.list comes up, uncomment (remove the #) from the lines that begin "deb" or "deb-src".

Then run ```
sudo apt-get update
``` which will update the package management system, allowing you to install more, followed by ```
sudo apt-get install xmms-mad xmms-mp4 xmms-flac
```

Audacity, though I have never tried it, is supposed to be a nice audio editor. Its available from the repos with apt-get, in the form shown above. Theres also kwave, but again, I have no experience with audio editing.

BTW, hows dapper?

Cheers,
Paul

---

### Post by Kevin_Vortex on 2006-04-11
Dapper is a dream and a half.
Thanks a tonne for the help. :)

---

### Post by Kevin_Vortex on 2006-04-11
E: Couldn't find package xmms-mp4
everything else worked like a charm...

Now all I have to do is figure out Icecast 2 for my net radio venture

---

