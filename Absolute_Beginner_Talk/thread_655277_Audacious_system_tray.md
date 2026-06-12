---
title: "Audacious system tray?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2008-01-01
I recently started to use audacious as a replacer for xmms or winamp and like it, but there is one thing I haven't underastand and it how I make it so it only show a system tray. Can it be done?

Similar to the system tray in winamp.

---

### Post by logos34 on 2008-01-01
**Status Icon 0.4** (--> audacious-plugins pkg) is what you're looking for, I believe.

Preferences>plugins>general tab

---

### Post by SpinningAround on 2008-01-01
It's almost what I'm looking for but I can't seem to make the window tab disappear so it only show the tray.

---

### Post by logos34 on 2008-01-01
> **SpinningAround said:**
> It's almost what I'm looking for but I can't seem to make the window tab disappear so it only show the tray.

click on the tray icon a few times--it goes away (or maybe you have to minimize first...play with it)

---

### Post by SpinningAround on 2008-01-03
Great it's working :D

---

### Post by andrewabc on 2008-01-25
Hello. I cannot find this plugin.
I am using Hardy, I have audacious 1.4.5 installed and audacious plugins-extra 1.4.4 installed.

I want to get rid of it from the window list. I have AWN installed, so I can just click on that icon to start/show/hide audacious.

It is not listed at [http://audacious-media-player.org/index.php?title=Plugins](http://audacious-media-player.org/index.php?title=Plugins)

---

### Post by mbsullivan on 2008-02-12
> Hello. I cannot find this plugin.
I am using Hardy, I have audacious 1.4.5 installed and audacious plugins-extra 1.4.4 installed.

I want to get rid of it from the window list. I have AWN installed, so I can just click on that icon to start/show/hide audacious.

It is not listed at [http://audacious-media-player.org/in...?title=Plugins](http://audacious-media-player.org/in...?title=Plugins)

Perhaps it doesn't support 1.4.5? I have audacious 1.3.2 installed (through Gutsy repositories) and Status Icon 0.4 shows up and works nicely. I've attached the library file for your use (perhaps)... untar it and place it @ /usr/lib/audacious/General/

If it turns out that the plugin doesn't work with the version in the Hardy repository, you could consider apt-pinning audacious to work from the Gutsy repository.

Hope this helps!
Mike

** Note: I installed audacious 1.4.5 today (which includes the "audacious", "audacious-plugins", and "audacious-plugins-extra" packages), and Status Icon 0.5 was present under the General Tab **

---

### Post by andrewabc on 2008-02-21
I notice this now as well. There is now a systray icon. But there is also a taskbar icon for the window. How do I get rid of it from showing up on taskbar (window list).

I currently have an icon in AWN, and now systray. Also showing in window list along with all my other open programs, but I do not want it shown there. Any way to hide it from showing there?

EDIT:
Clicking on sysraty icon hides audacious , along with it showing in window list. Doing this also crashed AWN.
I want the audacious player to be shown, but I do not want it shown in window list.

---

### Post by dahouse on 2008-03-03
I think audacious is awesome, small, light, great and my fav linux song player.

Like everybody is saying, the only problem is tray support.

I got the plugin working, but whenever I minimize audacious, it minimizes to the taskbar, not the tray icon. How do youchange this?

---

### Post by invizibility on 2008-03-14
Simply click on the Audacious icon in the system tray/notification area. That should do the trick.

---

### Post by andrewabc on 2008-03-22
> **invizibility said:**
> Simply click on the Audacious icon in the system tray/notification area. That should do the trick.

Yes. It hides it from the panel and also from showing up. I do not want it in the panel area, but I do want to see the player. But this is not possible.

---

