---
title: "Reinstall Firefox?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by radioraheem on 2006-02-01
Ubuntu rocks.  Yeah, I'm a less-than-48-hours newb.  But I'm learning.

In the name of learning I tried to install firefox 1.5 using the instructions here:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I should have tried Automatix :(

Anyway, now my copy of Firefox is working but not very well.   Basically what I want to do is completely reinstall it.  My bookmarks are backed up elsewhere and I don't really care about saving anything else in the profile.

Any tips?

Thanks

---

### Post by steve.horsley on 2006-02-01
You don't say what's not working well, which makes answering a little difficult.

Reinstalling firefox would consist of unpacking the tar.gz into /opt again. That will over-write the firefox binaries, but probably make no difference at all.

If a configuration option is giving trouble, your personal settings are stored in **~/.mozilla/firefox**, and you can rename this directory temporarily, or just delete it (while firefox is not running) to get back to the default settings. If you want to manipulate this directory with the nautilus file manager then you will need to press Ctrl-H to enable seeing hidden files and folders.

---

### Post by Ted D. on 2006-02-01
I have reinstalled Ubuntu for the same reason. My firefox profile settings were saved to a CD. After installing ubuntu again, I install firefox via automatix and imported my bookmarks. All worked fine.

Ted D.

---

### Post by Lord Illidan on 2006-02-01
[quote=Ted D.]I have reinstalled Ubuntu for the same reason. My firefox profile settings were saved to a CD. After installing ubuntu again, I install firefox via automatix and imported my bookmarks. All worked fine.

Ted D.[/quote]

Reinstalled Ubuntu? Whew... what a lot of hassle for nothing..imho..

To the OP: What kinds of problems are you having? Crashes, etc?

---

### Post by towsonu2003 on 2006-02-01
Try running firefox from a terminal using ```
firefox -safe-mode
```
If it is running without problems now, you have a problem with the extensions or the theme. If you have problems in *safe* mode as well:
[quote=Lord Illidan]To the OP: What kinds of problems are you having? Crashes, etc?[/quote]

As for the [quote=radioraheem]Basically what I want to do is completely reinstall it[/quote]
the instructions to uninstall are here [https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c](https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c)
this is the 5th section in the ubuntu wiki page.

---

### Post by Evolution-06 on 2008-07-03
> **steve.horsley said:**
> You don't say what's not working well, which makes answering a little difficult.

Reinstalling firefox would consist of unpacking the tar.gz into /opt again. That will over-write the firefox binaries, but probably make no difference at all.

If a configuration option is giving trouble, your personal settings are stored in **~/.mozilla/firefox**, and you can rename this directory temporarily, or just delete it (while firefox is not running) to get back to the default settings. If you want to manipulate this directory with the nautilus file manager then you will need to press Ctrl-H to enable seeing hidden files and folders.

this worked perfectly! thanks! i was getting very mad at firefox!

---

