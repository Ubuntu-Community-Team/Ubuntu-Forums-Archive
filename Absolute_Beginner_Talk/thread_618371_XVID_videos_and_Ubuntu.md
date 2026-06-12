---
title: "XVID videos and Ubuntu?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by NthgToFear on 2007-11-20
Hi everyone! 

I installed Ubuntu 7.10 on an older PC I have and I'm having an issue playing XVID videos. They skip and stutter like crazy and are pretty much unwatchable. I'm using Totem to play them because I can't get VLC to work when pulling the video off my Windows shared drive. CPU usage is up between 60-80% which seems really high, especially considering that it's around 30% in WinXP Pro on the same machine.

The box's specs are...

Athlon XP 1800+
1GB RAM
GeForce 4 64MB

Any help would be appreciated. I really like Ubuntu so far but if I can't get the vids to work right then it's pretty much useless to me... :(

-Matt

---

### Post by Inxsible on 2007-11-20
to state the obvious :

Have you installed all the required codecs via the medibuntu repos?

Here's a [link]("https://help.ubuntu.com/community/Medibuntu") to get you started, if you haven't done so yet.

---

### Post by NthgToFear on 2007-11-20
> **Inxsible said:**
> to state the obvious :

Have you installed all the required codecs via the medibuntu repos?

Here's a [link]("https://help.ubuntu.com/community/Medibuntu") to get you started, if you haven't done so yet.

Since I've never heard of that before, I'm going to go with no.

Thanks!!! I'll give it a shot!!!

The only codecs that were installed where 3 (all starting with gstream I think) that Totem wanted to install the first time I opened one of the videos.

---

### Post by Inxsible on 2007-11-20
> **NthgToFear said:**
> Since I've never heard of that before, I'm going to go with no.

Thanks!!! I'll give it a shot!!!

The only codecs that were installed where 3 (all starting with gstream I think) that Totem wanted to install the first time I opened one of the videos.yeah you need the libdvdcss2 and libdvdread from those repos.

Good Luck !

---

### Post by NthgToFear on 2007-11-20
I just tried it and CPU usage still hovers between 65 and 80%. However I just noticed that, when scrolling through this page with nothing else open, CPU usage hit 91%. That can't be right, can it...?

Is it possible my CPU isn't running at full blast?:confused:

---

### Post by NthgToFear on 2007-11-24
I just checked and the CPU is runnung at 100%.


Anyone have any other ideas?

---

