---
title: "Searching for wireless networks"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-03-08
I just installed ubuntu today, and my wireless card is up and working. How do I search for local wireless networks?

---

### Post by schwascore on 2007-03-08
download wifi-radar from the repo's.  Great little program.

---

### Post by Casla on 2007-03-08
to do a scan on the wireless interface

```
iwlist scan
```

to configure wireless interface, use

```
iwconfig
```

you may want to go through the manual for those commands

```
info iwlist
```
```
info iwconfig
```

It took me couple of weeks to setup my wireless, i guess coz i m completely new to linux and not that bright or luck in configuring stuff.

But the post that helped me most in setting it up is this one:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Very very good post.

in addition, if you want to learn more on how linux does wireless encryption etc, have a look on the 'wpa_supplicant' command.

actually, there are a list of useful commands in the end of that post, which are all very useful to look through.

Hope that will help, and good luck!

---

