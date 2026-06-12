---
title: "macbook 5,2: how to prevent automatic adjustment of display brightness?"
date: 2009-06-12
forum: Apple Hardware Users
---

### Post by cerbmuc on 2009-06-12
hi forums,

is there any way of disabling the automatic adjustment of the display brightness for the macbook 5,2?  i am using a fresh install of jaunty with the latest nvidia-drivers and it always will set my brightness to a very low level a few minutes after i adjusted it to fit my taste.

i then have to manually raise it again, just to wait for it to do stupid again.  this happend two times since i started writing this post.

any help would be appreciated, this is driving me nuts :-(

/w best regards,
gerd

---

### Post by cerbmuc on 2009-06-12
hi folks,

nevermind, i just found the setting!

/w best regards
gerd

---

### Post by UbuCocu on 2009-09-08
> **cerbmuc said:**
> hi folks,

nevermind, i just found the setting!

/w best regards
gerd

Would you mind sharing the setting with us?

Many thanks!

---

### Post by jrusso2 on 2009-09-10
I use a freeware application called caffeine that keeps it awake while I am working esp when not running on battery.

---

### Post by magicfab on 2009-09-14
You should be able to disable this by running gconf-editor

Then apps > gnome-power-manager -> ambience > disable.

---

### Post by caue.rego on 2009-11-21
> **magicfab said:**
> You should be able to disable this by running gconf-editor

Then apps > gnome-power-manager -> ambience > disable.
Thanks a lot for sharing this info! I've never seem that configurator panel before, and it also seem to have fixed my issue. :)

---

### Post by caue.rego on 2009-11-21
celebrated too early... problem persists. exactly same as cerbmuc, except it started when I've installed karmic and I'm on a regular intel PC a MSI.

I'm almost blindly guessing it might be kernel issue, I'll try booting older kernel next time.

edit:
Well, no older kernel fixed the issue, so it's definitely something that was installed with the 9.10 upgrade. I didn't have this issue before and if I boot from 9.04 live cd it also does not happen. Anyone can tell what it could be?

edit2: now I'm sure it is the gnome-power-manager (version 2.28.1) becaues the problem never happens when I disable it (open System Monitor and stop the process). next step: fixing it or using another version. (filled a bug about this at [https://bugs.launchpad.net/bugs/491595](https://bugs.launchpad.net/bugs/491595) but I've also found valuable info on [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910) after reading [https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug](https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug) )

---

### Post by caue.rego on 2009-12-07
this actually solved it for me! [https://bugs.launchpad.net/gnome-power/+bug/415023/comments/195](https://bugs.launchpad.net/gnome-power/+bug/415023/comments/195)

---

