---
title: "VLC and codecs"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by fullmetalgerbil on 2007-12-27
I tried to play a DVD with Totem and no luck-even after installing libdvdread3 (I also have the restricted extras package installed)-so I tried Xine, still no luck. Scoured some threads here then decided to try VLC and made it my default player. It didn't work. Are there codecs I need for VLC? 
I'm very new at this, I've only been running ubuntu for a few days, so I know very very little about using the terminal. Hopefully this can be fixed fairly easily as my n00bness might overload on a complex solution.

---

### Post by taurus on 2007-12-27
See if this link helps.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by oldos2er on 2007-12-27
[https://help.ubuntu.com/7.10/musicvideophotos/C/video.html](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html)

---

### Post by AndyCooll on 2007-12-27
Totem usually defaults to using the gstreamer plugins, for which the gstreamer0.10-ffmpeg is a good one to start with. After that, have you tried installing libdvdcss2?

:cool:

---

### Post by fullmetalgerbil on 2007-12-27
I went to the link posted in the first reply, followed another link to the index of /pool/free/libd/libvd/css, but there seems to be a ton of possible versions of libdvdcss and I'm not sure which one to use-I'm guessing one of the i386 ones as I have an x86 processor, however I'm not sure

---

### Post by crjackson on 2007-12-27
Okay, I assume you are using Gutsy 32-bit here...

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 
sudo apt-get install w32codecs
sudo apt-get install gxine
sudo apt-get install totem-xine
sudo apt-get install xine-ui
sudo apt-get install libdmx1
sudo apt-get install libxine1
sudo apt-get install libxine1-ffmpeg
sudo apt-get install libxinerama1
sudo apt-get install totem
```

---

### Post by fullmetalgerbil on 2007-12-27
Thanks I'll try it-only I noticed totem in the command, I'm trying to use VLC...no,wait, I'm trying to use whatever will work. I'll see how things work out.

---

### Post by fullmetalgerbil on 2007-12-27
Ok, I entered the first two commands, everything went great-however I'm not sure what to do with all the other commands in the third section, enter all of them or just the install libvdvcss2 one?

---

### Post by fullmetalgerbil on 2007-12-27
Well, I decided to use all the commands and VLC plays DVDs spectacularly. I haven't tried with totem or xine yet, but I'm sure they'll work too. Thanks so much for the help especially crjackson for providing the commands.

---

### Post by Tango_Down on 2007-12-27
All of them individually, it is a list of different codecs and media players. Some of them are better than others, you probably already have most of them, but they likely need a reinstall just to be sure they work with the new codecs.

---

### Post by crjackson on 2007-12-28
> **fullmetalgerbil said:**
> Well, I decided to use all the commands and VLC plays DVDs spectacularly. I haven't tried with totem or xine yet, but I'm sure they'll work too. Thanks so much for the help especially crjackson for providing the commands.

Glad I could help.  Don't forget to click the thanks button (star) next to the quote button in the my post.

---

### Post by meindian523 on 2007-12-28
Jack,that's blatant self-promotion........

edit:
@OP
Please mark thread as solved

---

### Post by billgoldberg on 2007-12-28
Use this to install the proper dvd and win32 codecs for totem. It's also a back-up program and alot more too.

[http://ubuntuforums.org/showthread.php?t=613462&highlight=ubackup](http://ubuntuforums.org/showthread.php?t=613462&highlight=ubackup)

But I also think that installing libdvdcss2 from synaptic should do the trick.

---

