---
title: "Cabextract Needs to Extract"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-11
I'm completely new to the command line and after installing cabextract, am now under the impression that it's not a GUI app?

If so, I have a file called WMP54GS_20050406.exe that I need to get the .inf file out of.  If someone could explain how I utilize cabextract to open this .exe, that would be great.  

Thanks :)

---

### Post by tallman9 on 2007-03-11
try opening it with wine

---

### Post by siciliancasanova on 2007-03-11
Wine tells me to extract it in c:/linksys

When I tried to extract it to my desktop, Wine wouldn't do it

I need it for ndiswrapper

---

### Post by msak007 on 2007-03-11
> **siciliancasanova said:**
> Wine tells me to extract it in c:/linksys

When I tried to extract it to my desktop, Wine wouldn't do it

I need it for ndiswrapper
Wine usually maps your /home directory to a drive letter. Run

```
winecfg
``` and then go to the "Drives" tab to see where it mapped it. You can change the directory and try to extract it to your Desktop. For example my /home directory is mapped to drive letter D, so I would choose D, drill down to my user folder, then the Desktop (or whatever other folder I desire).

The alternative is to let it extract to "C:\Linksys" - this folder will be located in the **.wine** folder (hidden) in your home folder. The Windows file structure of the Wine environment is contained in that folder, sort of like a virtual Windows if you will. If you enable hidden folders in Nautilus, when you go to your home folder you'll see one called .wine. If you let it extract to C:\Linksys, the path would be

/home/<user name>/.wine/drive_c/Linksys

Hope this doesn't confuse things, let us know how it works out or if you need more help.

---

### Post by siciliancasanova on 2007-03-11
Thanks a lot.  After 2 Days, that solution got my wireless card working in 2 minutes.  Thanks a lot.  I'm really excited about Ubuntu and the switch over to it.  I've been having a lot of fun.  :)

---

### Post by msak007 on 2007-03-11
Glad it helped. A lot of people have problems getting ndiswrapper / wireless to work, so it's good to hear the worst of your problems was getting the drivers to extract :). I was really excited when I first switched over a year ago, and I still am. It's fun learning something new everyday. Have fun.

---

