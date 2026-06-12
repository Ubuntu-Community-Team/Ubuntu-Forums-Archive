---
title: "Missing Application Icons"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Big Gaz on 2007-10-25
Hi I'm only a few days into using Ubuntu and Linux for that matter.

I have just loaded Konqueror, which in turn has loaded a shedful of other programs, many of them located in the applications>other location. But the majority have not icons?

Does anyone know why and how I can get the icons back?

Thx in advance

---

### Post by Happy_Man on 2007-10-25
Konqueror is a KDE application. Now is an excellent time to enlighten you about what that statement means. If you already know, sorry, but hey, a newbie could be reading this right? :)

There are many Desktop Environments (DEs) that can be run on top of X, which is the name of the backend for the display functionality of Linux. Two of the big ones are KDE and GNOME. 

KDE is based on the Qt toolkit, and uses KDE libraries to execute background processes. GNOME is based on the GTK+ toolkit and uses GNOME libraries to execute background processes. That's why if you install a GTK+ app (one that says, this blends in well w/ the Ubuntu desktop), you may only need to download a few KB of files. All the backend libraries are already installed, why install them again? 

(Sidenote: this, by the way, is a crucial difference between Windows and Linux. Every .exe in Windows comes with its own set of libraries, even if they are installed already. So you may need multiple copies of the same backend running, eating up RAM. Not so in Linux. Every library is installed only once, and is *shared* by the apps running. Lean and mean.)

But if you install a KDE app, as you have already seen, it'll download all the backend libraries that all KDE apps need, because they're not already installed. Of course, you'll only need to download them once, but still. 50+ MB downloads are looong. Konqueror may be even worse, since it's a filemanager and so needs special kioslave libraries also. Kioslaves are little applet-like things that give Konq and other KDE apps extra functionality. GNOME doesn't know what to do with all these new apps (generally they're background apps that don't need icons), so it displays them in the menus. They don't come with any sort of icons, though. Also, KDE apps run/load slower in GNOME, since they're not running in their native DE. So be prepared for that. 

Whoof, that's a lot! Hope this helps!

---

### Post by Big Gaz on 2007-10-25
Thx Happy Man,

Thats both a speedy and detailed reply. Much appreciated.

Thx again...

Big Gaz

---

