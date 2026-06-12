---
title: "Gnome Crashes When Loading"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-04-08
First, sorry if this has been posted before - it was hard searching for such a generic problem. I'll try to explain as much as I can:

The basic problem is that I cannot load Gnome. GDM comes up perfect. I log in, the Gnome splash screen comes up, and it appears to load each thing fine (it goes through all the icons). It then loads up my panel (I only have one). But....it just shows the blank spot where the panel is supposed to be. Before it loads the Application menu / System tray / etc, it crashes on me. I get a black screen for a while, then the nVidia logo appears, and I am back at GDM. There are no error messages or anything.

I have the nVidia drivers + Beryl installed, but:

1) I've had them for a looong time, and have only had problems when updating kernels (I keep my computer updated frequently, so that shouldn't be a problem), and
2) Although Beryl-Manager is set to auto-load (as it always has), my default DE is Metacity, so it doesn't even load Beryl on boot.

The biggest change I made before this happened was that I added a couple of programs to load on startup. However, I went into a console and deleted the two *.desktop files in ~/.config/autostart, rebooted my computer, and to no avail.

What should I troubleshoot next? The last update I had was exaile (svn) and another program (maybe Automatix), but it wasn't anything major. Sorry for the lack of details - it gave me no errors at all during the entire time.

---

### Post by tonyr1988 on 2007-04-08
Well, I removed the beryl-manager.desktop autostart file, and everything seems to be working perfectly. I'm not sure what happened to it (AFAIK I didn't update it at all, even though I'm using the svn Beryl), but it's working now, and that's all that matters.

---

### Post by tonyr1988 on 2007-04-09
Actually, the problem is worse than I thought. Gnome no longer crashes when loading (ever since I disabled beryl-manager from autostart), but it still crashes when I run beryl-manager or True Combat:Elite (a full-screen game).

I haven't had problems with either one until now. An update to beryl-manager could've slipped in (I use SVN), but TC:E hasn't been touched since installation. When running from the Terminal, no errors are shown - it just Ctrl+Alt+Backspaces, dumps me to a console for a little bit, and re-loads GDM.

I don't know where to start. I really don't want to do a fresh install just to get something like this working. Any ideas?

P.S. Sorry for triple-replying to myself.

P.P.S. I noticed that it always occurred when I ran *any* full-screen applications. I thought it was maybe my nVidia drivers. I re-installed and everything works perfectly - I can't believe I didn't think of that sooner. But...I was able to try out envy's new GUI...pretty impressive.

---

