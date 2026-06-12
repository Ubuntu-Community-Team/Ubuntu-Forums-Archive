---
title: "Playing DVDs"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Colro on 2007-10-13
I'm trying to play a DVD right now and Totem asked me to download some codecs. I let it do its thing. Now, however, it still won't work and says:

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media.

What can I do to fix it? What plugins do I need? As I said, I already let it install the codecs it needed.

---

### Post by Abild on 2007-10-13
Have you tried playing the DVD with VLC?

---

### Post by Colro on 2007-10-13
No, I'll install that and try it.

---

### Post by Colro on 2007-10-13
VLC opens the DVD, but it's all messed up with green distortion all over it and it closes itself a second later.

[img]http://blackhawkit.com/c0ld/dvdtest.png[/img]

---

### Post by Pumalite on 2007-10-13
sudo apt-get install ubuntu-restricted-extras

---

### Post by Colro on 2007-10-13
Still having the same problems after installing all that.

---

### Post by Colro on 2007-10-13
bump

---

### Post by skompier on 2007-10-13
I tried to play a DVD in Gutsy after I read your post and I got them same message. I got DVDs to play in VLC by doing the following:

I removed Totem via Add/Remove

Installed the CSS codecs via terminal

```
sudo apt-get install libdvdcss2
```

Reinstalled Totem via Add/Remove

I also made sure gstreamer stuff is also installed

My DVD started playing in VLC. Not sure if the above order had anything to do with it. I think I just stumbled across the magic combination. Oh yea...I also held my left foot about  6 inches off the floor while sticking my index finger in the right ear...viola! \\:D/

---

### Post by Colro on 2007-10-13
I can't uninstall totem for some reason, it says other programs depend on it.

---

### Post by por100pre1 on 2007-10-13
If you are using Feisty read [this]("http://ubuntuforums.org/showthread.php?t=413624").

---

### Post by Colro on 2007-10-14
> **por100pre1 said:**
> If you are using Feisty read [this]("http://ubuntuforums.org/showthread.php?t=413624").

Thank you very much. VLC is working now, although totem isn't. Good enough for me, though.

---

### Post by skompier on 2007-10-14
> **Colro said:**
> Thank you very much. VLC is working now, although totem isn't. Good enough for me, though.

Glad to hear it. I can't get Totem working either, but no big deal. VLC works...movie time. :popcorn:

---

### Post by tgbrowning on 2007-10-14
It turns out that there are a number of different pieces you need to get Totem (and the others) to work on most DVDs.  Libdvdcss is one, but you also need the win32codec, and several different gstreamer packages to boot.  

Note that you cannot have both the gstreamer version of the player and the regular totem version of the player both installed. I use the totem version because it has support for dvd menus.  Get into the package manager, do a search for codec and a search for dvd, scroll through it and mark pretty much anything that looks like it acts as a codec. You're looking for ones that say they allow you to play particular formats.

As has been pointed out, the libdvdcss package MAY be illegal in some places. It's not part of the Ubuntu universe or multiverse. Hit Wiki and read all about the reasons why and where you can find stuff. Medibuntu is the web site you'll be headed for to grab libdvdcss.

Browning>>>

---

