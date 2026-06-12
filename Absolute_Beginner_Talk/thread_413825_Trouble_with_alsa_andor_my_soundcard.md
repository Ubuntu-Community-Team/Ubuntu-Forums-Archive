---
title: "Trouble with alsa and/or my soundcard"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mrfredman on 2007-04-19
I've been having ongoing soundcard issues, it refuses to make a sound. I've managed to get a bit farther with this, but this is my latest problem, and I don't know what to do.

I cant get alsa to run. When I type alsamixer in the command line this is what I get:

alsamixer: function snd_ctl_open failed for default: No such device

Does this mean I installed it wrong? Or is this still a hardware issue or something?

Kmix is currently my default audio mixer (Im running KDE), And that refuses to recognize any soundcards, but my other question is: How to I make alsa my default sound mixer? Because whenever I hit the volume up or down keys on my keyboard kmix automatically opens.

Help?

---

### Post by Seisen on 2007-04-19
Go to System>Preference >Sound and you should be able to change it their. You can try to do this in the terminal to get alsa if you don't have it.

```
sudo apt-get alsa
```

---

### Post by mrfredman on 2007-04-19
Thanks, but thats not the problem. I already downloaded alsa, and I know it exists on my hard drive. It may not be configured properly or something though, as I just downloaded it a few days ago. 

Assuming I do have alsa, how would i configure my soundcard with it?

---

