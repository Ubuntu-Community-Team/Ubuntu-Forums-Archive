---
title: "pandora and youtube?"
date: 2007-08-01
forum: Apple PPC Users
---

### Post by mexiloco on 2007-08-01
I installed fiesty today and i cannot find the plugins for adobe flash player?  Do they even exist?  I'm on an eMac G4 btw.

---

### Post by Malh on 2007-08-01
Try [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by gvigorus on 2007-08-01
Get Gnash, VLC and install VideoDownloader: [http://javimoya.com/blog/youtube_en.php](http://javimoya.com/blog/youtube_en.php)
Then save .flv to your desktop and watch them in VLC

---

### Post by stmiller on 2007-08-01
All of your answers are in the PowerPCFAQs:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Please try the new gnash 0.8.0, which plays youtube

---

### Post by mexiloco on 2007-08-01
i installed gnash via Add/Remove applications and flash still does not work.  Do I need to reconfigure something in the terminal?

---

### Post by Auria on 2007-08-01
> **mexiloco said:**
> i installed gnash via Add/Remove applications and flash still does not work.  Do I need to reconfigure something in the terminal?


you need gnash 0.8.0 for this, i don,t think it's available in the repos (check the version)
even then many people have reported it not working on their computer, so it might be easier to use the video download

---

### Post by stmiller on 2007-08-02
> **mexiloco said:**
> i installed gnash via Add/Remove applications and flash still does not work.  Do I need to reconfigure something in the terminal?

Gnash 0.8.0 is now in the official repos- in Feisty Backports.

After you enable the Feisty-Backports like in the PowerPCFAQ, open a terminal and do
```

$ sudo apt-get install gnash

```
and it should install the new version 0.8.0

---

### Post by stmiller on 2007-08-02
Ah I just tried the Pandora site and unfortunately is does *not* work with Gnash 0.8.0. :-( 
I'll ask around on the Gnash dev list to see if they have any ideas.

---

### Post by mexiloco on 2007-08-02
Thanks you guys I REALLY appreciate the help and all, but i screwed up the sound files while in the terminal, so I think I'll just pick up a 500 MHz celeron box and install Xubuntu on it to use it as a small media server and for web browsing.  It should have more web funtionality than my eMac (which i use for photoshop and my heavier-weight apps).  Thanks a million anyway.

---

