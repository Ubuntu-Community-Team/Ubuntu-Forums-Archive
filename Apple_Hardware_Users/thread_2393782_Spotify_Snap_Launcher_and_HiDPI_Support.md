---
title: "Spotify Snap Launcher and HiDPI Support"
date: 2018-06-07
forum: Apple Hardware Users
---

### Post by trevorzenk on 2018-06-07
Hello all!

I have been working on setting up my favorite applications on Ubuntu installed on my MacBook Pro, I am no novice to Linux systems, but I have been struggling with finding a way to launch Spotify with HiDPI settings.  I installed Spotify via the Ubuntu Store (I prefer using apt-get, but spotify doesn't exist on Ubuntu's stock repos).  Upon launching Spotify, the UI was incredibly tiny.  I was able to make the UI an appropriate size by launching "spotify --force-device-scale-factor=2" from a terminal or run prompt, but I cannot figure out for the life of me how to run this command option through the gnome3 launcher.  "whereis spotify" returns "spotify: /snap/bin/spotify", but unlike a .desktop launcher file, I cannot modify this apparent binary file and simply add an environment variable or command option.  Anyone have success with this?  Bear in mind I have a 13 inch display so the larger elements appear far more natural and way more comfortable to read and navigate.

[ATTACH=CONFIG]280031[/ATTACH]Launched via run command
[ATTACH=CONFIG]280032[/ATTACH]Launched via gnome launcher

---

### Post by trevorzenk on 2018-06-08
I solved my issue after tinkering around a bit.  I installed alacarte and modified the spotify entry and inserted the option command folowing the bin file.  This resulted in the command field "env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/spotify_spotify.desktop /snap/bin/spotify --force-device-scale-factor=2 %U " and its behavior is what I wanted and expected.

---

### Post by hkiang01 on 2018-11-17
Thank you, trevorzenk, that worked for me.

If anyone is curious, I'm using a Dell XPS 15 9560 touch with Ubuntu 18.10.

---

### Post by baroncelli-gmail on 2018-11-27
> **trevorzenk said:**
> Hello all!

I have been working on setting up my favorite applications on Ubuntu installed on my MacBook Pro, I am no novice to Linux systems, but I have been struggling with finding a way to launch Spotify with HiDPI settings.  I installed Spotify via the Ubuntu Store (I prefer using apt-get, but spotify doesn't exist on Ubuntu's stock repos).  Upon launching Spotify, the UI was incredibly tiny.  I was able to make the UI an appropriate size by launching "spotify --force-device-scale-factor=2" from a terminal or run prompt, but I cannot figure out for the life of me how to run this command option through the gnome3 launcher

Just a note that Spotify supports a persistent option for scaling via ctrl+"+" and ctrl+"-": modifying the scaling via these two commands will set the value in a way that will get reloaded after restarts.

---

