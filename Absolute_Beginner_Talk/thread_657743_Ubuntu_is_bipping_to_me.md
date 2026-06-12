---
title: "Ubuntu is bipping to me"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mars2010 on 2008-01-03
Hello It is me again. Sometimes I watch some videos and when they are finish. There is a sound like bip and only stop when I restart the PC. Does anybody knows Why and How can I stop this? Please I need help.

---

### Post by steve8track on 2008-01-04
What video are you watching?  Is it online?  Is it streaming?  Is it on your hard drive?  What format is it?  Flash?  AVI?  DVD? etc...  What video player are you using?  VLC?  Totem?  Flash in Firefox, Opera, or Epiphany?  Are you running Compiz-Fusion or Beryl (the desktop cube/wall effects)?  Are you running XGL?

My first suggestion is to try VLC.

```
sudo apt-get install vlc
```

Also, is your sound working?  Is the video card working?  What are they?

I hope this helps.

---

### Post by mars2010 on 2008-01-05
I am watching on line videos and I use mplayer. I have VLC installed in my computer but is not as a plugin for firefox. If you know something please help me. Anyway thanks a lot steve8track.

---

### Post by oliviacond on 2008-01-05
how about disabling beep?

```

sudo gedit /etc/modprobe.d/blacklist

```
Then add this line to the bottom of the file, save, and exit.

blacklist pcspkr

Then run:
```
sudo modprobe -r pcspkr
```

---

### Post by mars2010 on 2008-01-05
It did not worked it.I still need help. The last command did show anything

---

