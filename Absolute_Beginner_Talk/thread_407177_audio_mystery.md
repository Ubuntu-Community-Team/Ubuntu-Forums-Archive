---
title: "audio mystery"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ve3rpm on 2007-04-11
I found that each an every time I boot up I need to reload this into the terminal.

sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss

For the life of me, I don't know why it doesn't stick for the next time that I boot up.  Any suggestions?  thanx Dan

---

### Post by ThrobbingBrain66 on 2007-04-11
> **ve3rpm said:**
> I found that each an every time I boot up I need to reload this into the terminal.

sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss

For the life of me, I don't know why it doesn't stick for the next time that I boot up.  Any suggestions?  thanx Dan

You can edit your /etc/modules file and add each of those modules to the list.  These modules are then loaded at startup.
```
gksu gedit /etc/modules
```

---

### Post by ve3rpm on 2007-04-11
okay, then, I gave it a whirl, and the puter gave me this response

(gedit:6213): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by bobplano on 2007-04-11
i think that is fine since it is just a warning but if you really want to confirm its all right then you can use gksudo or even regular sudo(but it is not really recommended)

---

### Post by ThrobbingBrain66 on 2007-04-11
> **ve3rpm said:**
> okay, then, I gave it a whirl, and the puter gave me this response

(gedit:6213): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

It's a known bug.  Everyone gets that message, nothing to worry about though.

The explanation can be found at the bottom of this page:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ve3rpm on 2007-07-13
Well, I cured the problem.  Bought a barebones puter, and wow what a difference.  Now if I just get permission to write to my hdd's I'll be thrilled.  Thanx All

---

