---
title: "Gnome Settings Daemon problem after upgrading to 7.10"
date: 2007-11-16
forum: Apple PPC Users
---

### Post by rrwood on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255](https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/163255) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After upgrading to 7.10, I ran into a problem such that when I log-in, I soon have a dialog box pop up informing me that the Gnome Settings Daemon failed to load properly.  The exact text is:

"There was an error starting the Gnome Settings Daemon.

Some things, such as themes, sounds, or background settings may not work properly.

The Settings Daemon restarted too many times.

Gnome will try to restart the Settings Daemon next time you login."


There are a lot of references to this problem in the forums, including many suggestions for fixing it that do NOT work.

In my case, the fix was to downgrade liboil.  Once I did that, then the settings daemon is fine.  Behind the scenes, the settings daemon was trying to load GStreamer, which was failing.  Apparently GStreamer depends on liboil.

I'm not sure what the probably is with the latest liboil package, but hopefully someone will find and fix the problem soon.  In the meantime, with the downgraded liboil package, the update manager is very unhappy and refuses to do its thing.

---

### Post by flabdablet on 2008-03-01
Hope [this workaround]("https://bugs.launchpad.net/ubuntu/+source/liboil/+bug/72814/comments/29") helps somebody.

---

### Post by stream303 on 2008-03-02
I did some searching and found some people had good results by installing

**dbus-x11**

(lowercase X).  I don't know if this really fixes the problem, was a forgotten package, or is a package that Ubuntu is trying to deprecate.  But for those who have tried it, they say it works.

I didn't have the problem, but in the interest of science, I found that this package was not installed on my Gutsy system, so I apt-get installed it just to see what would happen.  Glad to report nothing, so maybe for me it's a placebo. :)

I've been reading about it curing other mysterious hangs, so I wonder if this would also fix the sound problem some users experience at gnome startup rather than disabling ESD.  Pure speculation here since I can't test it since I don't have the problem.

---

### Post by smomanyi on 2008-03-31
The problem is the xserver-xgl. Just remove it with this command "apt-get remove xserver-xgl"

---

