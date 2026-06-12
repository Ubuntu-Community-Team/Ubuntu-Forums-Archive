---
title: "No Sound O_o"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by necronzero on 2008-03-21
Even though i see the volume control and can access it, I can't hear anything... I tried listening to a Youtube video and couldn't hear anything... went to Gametrailers and same... What can i do to fix this???

Got a Satellite P105-SP921
Thanks In advance

---

### Post by Sef on 2008-03-21
Are you using a 32-bit or 64-bit system?  Are you using Firefox as your browser?  I know there has been a problem with sound. Here's [post]("http://ubuntuforums.org/showthread.php?t=321048") on how to fix it.  See post #2 or read below.

Adapted from Divague's directions:

Applications > Accessories > Terminal

```
sudo apt-get update
```

```
sudo apt-get install alsa-oss
```

```
gksudo gedit /etc/firefox/firefoxrc
```

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

Note: In my /etc/fire/fox/firefoxrc:   FIREFOX_DSP="none"

---

### Post by spiderbatdad on 2008-03-21
You could open the volume controls and make sure PCM and Master are up. If no luck post the result of asoundconf list by running it in the terminal.

---

### Post by spiderbatdad on 2008-03-21
see this post:
[http://ubuntuforums.org/showthread.php?t=589820](http://ubuntuforums.org/showthread.php?t=589820)

or:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

