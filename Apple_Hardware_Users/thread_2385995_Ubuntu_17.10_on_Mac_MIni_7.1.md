---
title: "Ubuntu 17.10 on Mac MIni 7.1"
date: 2018-02-27
forum: Apple Hardware Users
---

### Post by Uvunter on 2018-02-27
Hello.

Well, I decided to do a little experiment on my Mac Mini 7.1 (Late 2016, if I'm not mistaken: 1,4GHz, 4GB RAM, etc.), just because I was bored and I missed GNU/Linux a lot. So, I followed some tutorial to dual boot MacOS and Ubuntu. I thought that there were some compatibility problems, but no. I just had to write two or three commands to get my wi-fi work, no big deal.

But there are some little troubles, which I don't know how to solve:

1) I've some Steam games, which I can play well on MacOS High Sierra, but I can't play on Ubuntu 17.10. It just appears a blank screen, or even nothing. My videocard is an Intel HD Graphics 5000.

2) When I keep opened Firefox, Spotify, LibreOffice, and I try to play a Steam game, Ubuntu freezes, and I can't do anything. No mouse, no keyboard, nothing, and I must force a shutdown by holding the power button. I've not installed a swap partition, I only have the swapfile installed by default.

---

### Post by kerry_s on 2018-02-27
most likely your cpu is to slow to keep up.

have you logged out & selected gnome xorg
the default wayland has a lot of issues with some apps

---

### Post by kevin160 on 2018-02-28
> **kerry_s said:**
> most likely your cpu is to slow to keep up.

Naw, an i5-4260U bursts to 2.7 GHz and should be fine for almost anything.  If you mean GPU, then, yes the integrated Intel graphics might be to wimpy for some games.  But if you've been running them on macOS on the same machine, I would expect performance to be similar.  

What games are you trying to run?

---

