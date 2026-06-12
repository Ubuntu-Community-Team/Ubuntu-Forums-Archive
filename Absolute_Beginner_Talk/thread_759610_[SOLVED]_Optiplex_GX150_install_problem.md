---
title: "[SOLVED] Optiplex GX150 install problem"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2008-04-19
OK ,so i'm trying to install 7.10 on an old Dell Optiplex GX150 and running into problems.

basically i cant get a display to work and want to "drop" to root terminal (via ctrl,alt,backspace) so i can
```
sudo dpkg-reconfigure xserver-xorg
```
and hope to get in via "vesa" mode.

How can i get down to terminal - it wont let me and i'm just about to take a hammer to this thing!

Here's a similar thread but this is not working for me , any ideas please.
[http://ubuntuforums.org/showthread.php?t=118359&highlight=gx150](http://ubuntuforums.org/showthread.php?t=118359&highlight=gx150)

---

### Post by gn2 on 2008-04-19
When you boot repeatedly tap Esc then select "Recovery Mode"

This runs with admin priviledges in text mode and will allow you to run
```
dpkg-reconfigure xserver-xorg
```

When your done type ```
shutdown -r now
```
Hopefully that should re-boot you to a working desktop.

For older hardware like your Optiplex and for tricky installations generally, I find that installing using the "Alternate CD" works much better.

---

### Post by SnakeHips on 2008-04-20
Finally got it going using these settings :-) using xubuntu alternateCD 8.04

hit "esc"
select "recovery mode"
at root prompt...
```
dpkg-reconfigure xserver-xorg
```
xserver driver = intel
identifier = intel corp 82815
colours = 24

```
shutdown -r now
```

......a nice surprise ,it went to network without any configuring and gave me 120 updates lol

---

