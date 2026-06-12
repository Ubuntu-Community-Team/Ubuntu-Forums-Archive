---
title: "New installation, not able to log in garphic mode"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by dosyl on 2008-01-22
Hi,
I just installed Ubuntu 7.10, 64 bits.
Before and now I have Win XP.
Win Xp is on: sda1
Recovery Win XP sda2
And for Ubuntu:
sda3 Extended
sda5 LinuxSwap
sda6 Linux -> /home
sda7 Linux -> /

I am to log without graphic mode, but not in graphic mode.
Ubuntu tell that I stay connected less than 10 secondes.
The user and password are goods because I can log when I do ctrl+alt+F1. :(

---

### Post by dcstar on 2008-01-23
> **dosyl said:**
> Hi,
I just installed Ubuntu 7.10, 64 bits.
Before and now I have Win XP.
Win Xp is on: sda1
Recovery Win XP sda2
And for Ubuntu:
sda3 Extended
sda5 LinuxSwap
sda6 Linux -> /home
sda7 Linux -> /

I am to log without graphic mode, but not in graphic mode.
Ubuntu tell that I stay connected less than 10 secondes.
The user and password are goods because I can log when I do ctrl+alt+F1. :(

Your graphics settings are probably not set up properly, do a forum search for "dpkg-reconfigure xserver-xorg" and you should get a list of detailed posts that can help you.

---

