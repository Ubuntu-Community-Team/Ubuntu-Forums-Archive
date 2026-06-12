---
title: "How do i play music/DVD's in ubuntu?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Shaun440 on 2008-02-06
ok I'm completely new to this. How do i play music (mp3, wma, AAC and the like) and DVD's in ubuntu?

Also, can I use the remote control that came with my old windows XP media centre computer?

Cheers
Shaun

---

### Post by obscur156 on 2008-02-06
Hi,install "ubuntu restricted extras " with add/remove or synaptic manager" and you should be able to play any kind of media.

VLC is very powerfull media player and can be install with add/remove or synaptic manager.

For your control of win xp,i dont think so.
Good luck,best regards.

---

### Post by wirawan0 on 2008-02-06
Here you go:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

For more restricted formats, go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Unfortunately you have to "do it yourself" (but the instruction is very clear).


Good luck,
Wirawan

---

### Post by oldb0y on 2008-02-06
You need restricted pluins for DVD's and such.

Try this in a terminal: ```
sudo apt-get ubuntu-restricted-formats
```

---

### Post by newlinux on 2008-02-06
> **Shaun440 said:**
> ok I'm completely new to this. How do i play music (mp3, wma, AAC and the like) and DVD's in ubuntu?

Also, can I use the remote control that came with my old windows XP media centre computer?

Cheers
Shaun

Yes you can use your remote with certain programs (mplayer and vlc to name a couple). Assuming you have an IR receiver, you just need to install and configure LIRC.

[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

Good luck and feel free to ask more questions as you get into it.

---

### Post by steveneddy on 2008-02-06
Here is[ the know it all guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") you are looking for.

---

### Post by ubuntu-freak on 2008-02-06
My simple cut and paste [how-to](http://ubuntuforums.org/showthread.php?t=661833) will help you. I've had great feedback.
 
Nathan

---

### Post by nikoPSK on 2008-02-06
get gstreamer codecs. for dvds, you need to do this:
```

sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

