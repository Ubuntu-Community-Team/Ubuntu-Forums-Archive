---
title: "New at linux"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by DGGARCIA on 2008-01-02
Hi all,

I've recently change to Ubuntu and erase windows once and for all. Now more less everything is working out all right. But there is 3 things that for the moment i don't know how to do. I hope u can help. Here they are:

Skyp   There is any program in the repositories???

Amule     How I get the servers???

The last question is how I put some subtitles in some videos I have. The subtitle file is .srt and i'm using Totem.

Thanks in advance for your help guys. I really appreciate it.

---

### Post by criskat777 on 2008-01-02
Hi, Use Frostwire instead of Emule. It's like Limewire P2P:popcorn:

---

### Post by BrianElliott0218 on 2008-01-02
:popcorn:
Try this link (and look around on the site!  It's a great place to find Linux versions or replacements for WinBlows and even OS X applications).
[http://linuxappfinder.com/alternatives?search_text=Skype](http://linuxappfinder.com/alternatives?search_text=Skype)
From the list there, it looks like there is a Skype for Linux and three alternatives as well.  They even give you the available Deb Repostiories to add to your apt so you can download it and update it directly.
Have fun!
~BE

---

### Post by hanniph on 2008-01-02
If you want to use subtitles, download VLC player. You can browser your subtitles under 
settings --> Preferences --> Video --> Subtitles/OSD.

---

### Post by ~LoKe on 2008-01-02
The subtitles should load automatically if they have the same name as the video files.

---

### Post by Ozitraveller on 2008-01-02
Skype

try here:
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by jken146 on 2008-01-02
Skype is in the medibuntu repository.  Add the repo ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) then install Skype with apt-get.

---

### Post by Hallvor on 2008-01-03
> **DGGARCIA said:**
> 
Amule     How I get the servers???


[http://peerates.net/peerates/index.html](http://peerates.net/peerates/index.html)

---

### Post by Mud.Knee.Havoc on 2008-01-12
If you want to burn the subtitles right into the movies (so you can never watch the movie without the subtitles), use this command (but modify it as you need):

mencoder -ovc xvid - xvidencopts fixed_quant=3 -oac copy -sub name.of.subtitle.file.srt -o movie.name.output.avi movie.name.input.avi

---

### Post by SOULRiDER on 2008-01-12
For viewing the videos with the subtitles I'd use VLC instead of Totem.

---

