---
title: "Firefox plugins, mplayer conflict with realplayer"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-04
Hi all,

first off now I can watch embedded files from sites but on BBC wesite it seems to get abit confused with realplayer. I've removed the totem plugins but do I need to remove the reaplayer plug. If so which command.

(Totem could not play embedded files well at all)

Thanks in advance.

---

### Post by buzzmandt on 2007-08-04
if you know what kind of media works from the bbc and what works you can go to preferences, content, manage file types and select what opens what media

---

### Post by philinux on 2007-08-04
Thanks but that does not alter embedded file type for some reason, already tried that

---

### Post by designwiz on 2007-08-04
To remove all files associated with real player use
> sudo apt-get remove --purge realplayer

Most of the video are flash based!

How to install Flash Player (Macromedia Flash) Plug-in for Mozilla Firefox 

Install using Synaptic Package Manager or aptitude
System-->Administration-->Synaptic Package Manager-->Search-->flashplugin-nonfree-->Mark for installation-->Apply
or (from command-line terminal): 

> sudo apt-get install flashplugin-nonfree

Hope this helps!

Peace Out \\//

---

