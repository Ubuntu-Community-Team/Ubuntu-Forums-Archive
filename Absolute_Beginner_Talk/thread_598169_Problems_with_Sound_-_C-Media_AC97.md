---
title: "Problems with Sound - C-Media AC97"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by AeroCross on 2007-10-31
I'm having a big issue here. I have a C-Media AC97 integrated sound card, and I can't hear a Sound. As far as I've seen, the drivers are correctly installed. I've installed and configured the ALSA packages (alsa-base, alsa-utils and alsa-oss) and nothing.The only think I can hear is a very VERY low sound, even when my speakers are full volume, and the Mixer is full (Via GUI and alsamixer)

Some info of my card:
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

I've already tried reinstalling and nothing, changing devices, nothing. I know it's unmuted, and full volume, connection cables, everything.
And now I don't know what to do. Anyone has any ideo what happens?
I would appreciate that a lot n.n
Thanks.

---

### Post by henklaak on 2007-10-31
Here are two pointers for you:

For the basic errors:
[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

For advanced problem solving:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Hope this works for you.

Gr. Henk.

---

### Post by AeroCross on 2007-10-31
None of those topics worked for me... The final thing I did was to update the ALSA Drivers.
Now it doesn't recognizes my Sound Card o_o

One curious thing was that like almost a year ago, I installed Ubuntu in this same computer, and the sound worked perfectly, without any kind of problems nor configuration.
I just don't know what's happening... t_t

---

