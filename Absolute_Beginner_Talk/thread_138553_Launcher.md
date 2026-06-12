---
title: "Launcher"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-03-02
Am using kubuntu breezy. I want to know whether its possible to run the launcher package within KDE. I tried to install the launcher with the command and i succeded in doing so. 

```
sriram@Home:~$ sudo apt-get install launcher
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  launcher
0 upgraded, 1 newly installed, 0 to remove and 174 not upgraded.
Need to get 22.7kB of archives.
After unpacking 127kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/universe launcher 0.86-1 [22.7kB]
Fetched 22.7kB in 2s (8893B/s)

Preconfiguring packages ...
Selecting previously deselected package launcher.
(Reading database ... 67849 files and directories currently installed.)
Unpacking launcher (from .../launcher_0.86-1_all.deb) ...
Setting up launcher (0.86-1) ...
sriram@Home:~$
```

But when i tried to run the command "launcher" in Run Window nothing happened not even error message popped up. Can anybody make out watz the problem?

---

### Post by jamyskis on 2006-03-02
Launcher is a command line program that directs its output there and requires you to state which file you'd like to open, for example "launcher spreadsheet.xls" will launch whichever program is configured for Excel spreadsheets. If there isn't, it will offer you a choice of programs to open it with.

If you try to run launcher from the "Run Program" command in the menu, the output that tells you that it needs a filename will be directed to NULL - in other words, you won't be able to see it.

---

### Post by daredevil on 2006-03-02
jamsyskis thnx for the info. But actually my requirement was to create a new Launcher similar to the option available in context menu of right click(on Desktop) in ubuntu. I dunno if its possible in kubuntu but just saw that in ubuntu and wanted to do(imitate) the same in kubuntu. Sorry if am silly. Any thoughts? 
Thnx in advance

BTW i think this post should be "kubuntu desktop" section

---

