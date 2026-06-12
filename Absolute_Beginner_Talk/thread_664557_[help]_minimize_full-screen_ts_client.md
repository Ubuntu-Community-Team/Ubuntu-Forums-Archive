---
title: "[help] minimize full-screen ts client"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by shmengie on 2008-01-11
so, in searching, i found [this](http://ubuntuforums.org/showthread.php?t=104993).  

okay, this works with visual effects turned off. if i'm on normal or extra, the window **tries** to minimize, but snaps back. anyone know of a way to make this work with visual effects enabled?

thx!

---

### Post by natirips on 2008-02-14
If you're using compiz, try intalling compizconfig-settings-manager in Synaptic, then go to System -> Settings -> Advanced Desktop Effects Settings and go through all of it, prehaps you can find some solution there.

---

### Post by JLevet on 2008-03-03
A solution I had success with when using Compiz and tsclient to and RDP-based TS in fullscreen was to simply right-click the task bar, select Task Manager, then users then disconnect my own session.

When ready to reconnect just click connect again :D

---

### Post by herda05 on 2008-03-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/152615](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/152615) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There are a links to the solution out there, though not easy to find. natirips is mostly correct:

> try intalling compizconfig-settings-manager in Synaptic, then go to System -> Settings -> Advanced Desktop Effects Settings

If you do an advanced search for legacy, you will see a setting called "Legacy Fullscreen Support". Uncheck it and then you can use the key sequence CTRL+ALT+ENTER to minimize the rdp session to a window. Doing it again goes back to fullscreen.

here's some of the links:

[Full Screen and TSclient]("http://www.steveneppler.com/blog/2005/12/07/full-screen-and-tsclient")
[remote desktop windows xp from ubuntu]("http://ubuntuforums.org/showthread.php?t=327984&highlight=tsclient+fullscreen")

---

### Post by shmengie on 2008-03-12
thx, herda! works like a champ!

---

