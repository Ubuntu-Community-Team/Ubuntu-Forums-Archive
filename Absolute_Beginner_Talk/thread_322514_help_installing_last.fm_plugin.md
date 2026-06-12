---
title: "help installing last.fm plugin?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by samlathan on 2006-12-20
Can someone help me install the Last.FM plugin on xmms? Any help is appreciated.

---

### Post by 23meg on 2006-12-20
What did you do to install it and how exactly is it failing?

---

### Post by slackjack on 2006-12-20
You install it via apt-get (assuming that the universe repo is enabled [enable from synaptic])

apt-get install xmms-scrobbler

---

### Post by samlathan on 2006-12-20
> **23meg said:**
> What did you do to install it and how exactly is it failing?
I didn't install the srobbler plugin yet, just xmms.

---

### Post by samlathan on 2006-12-20
> **slackjack said:**
> You install it via apt-get (assuming that the universe repo is enabled [enable from synaptic])

apt-get install xmms-scrobbler

Well it said the persmission is denied, which is odd. I THOUGHT I was root.

It said it was unable to unlock the administration directory..

---

### Post by samlathan on 2006-12-20
Errr, it says this now.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmms-scrobbler

I have it in my home folder.

---

### Post by samlathan on 2006-12-21
Argh, no one else has anything? This is really bugging me. :(

Nevermind, figured out something else.

---

### Post by 23meg on 2006-12-21
Make sure [the Universe repository is enabled]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html"), then type ```
sudo apt-get install xmms-scrobbler
```

---

### Post by samlathan on 2006-12-21
Heh, yeah I got it, thanks. :)

---

