---
title: "Firefox plug-ins."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by HarrisonHopkins on 2006-08-26
I tried the how-to of it, but none of the things listed appeared in Synaptic. Can someone tell me how to get them to work?

---

### Post by jordanmthomas on 2006-08-26
Which guide did you follow?

---

### Post by HarrisonHopkins on 2006-08-26
Hold on, let me find it...

[Here.]("http://http://ubuntuforums.org/showthread.php?t=135371")


Doesn't allow html.... darn.

---

### Post by jordanmthomas on 2006-08-26
There's a couple of ways you can go about getting the plugins.
I'm assuming you just need flash, java, and video plugins.

The easiest way is to use [Automatix]("http://www.getautomatix.com"), but a lot of people won't use it since it's not open source.

The other way is this:
1.  Enable multivers and universe repositories ([link]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories"))
2.  ```
sudo apt-get update
```
3.  ```
sudo apt-get install sun-java5-jre sun-java5-plugin flashplugin-nonfree mozilla-mplayer 
```
Read anhything that comes up and accept. (if you do indeed accept)
4.  ```
sudo update-flashplugin
```

This *should* work

---

