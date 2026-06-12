---
title: "WoW - DVD = problems"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-11-26
hi.
i've bought a world of warcraft DVD, and i cannot install it on my computer.
i've tried tu using this way

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Installing_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Installing_wine)

but- it worked with WoW on Cd, but- becouse one of my installation cd was corrupted (really corrupted) i bought dvd-version.
the problem is that on dvd there is no installer.exe (or any other exe file :o), but, so i really don't know how to start installation... i've got only this:

[anecia@localhost WoW DVD]$ ls
Installer Tome 2.mpq*  Installer Tome 5.mpq*  World of Warcraft (OS X).app/
Installer Tome 3.mpq*  Installer Tome 6.mpq*
Installer Tome 4.mpq*  Installer Tome.mpq*

but this dvd seems to work on windows- i.e autoplay is working, the installation menu is showing etc... even on process-manager on windows is a process 'installer.exe', so dvd is ok...
any suggestions?

wine is 0.9.47

---

### Post by Slakker on 2007-11-26
Try this page:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It sounds like you can install it on windows and copy it over from the windows partition somehow.  Good luck!

---

### Post by BrettA on 2007-11-26
Don't suppose you've tried looking at hidden folders? 

I think the command is Ctrl+H, but it will be in the Edit menu I think.
Other than that run the *.exe through Wine and it should install fine.

---

### Post by doowgof on 2007-11-26
If there is a installer.exe in windows, there must be one in Linux too.
Try to use search and maybe you can find it.
You can install wow into your windows partition and then copy it to wine's programs folder. If you don't have windows on your computer at all then install it onto a removable hard drive and copy it to wine's folder.

---

### Post by irate vermin on 2007-12-10
i encountered the same problem. I decided to try and use the installer.exe from the regular WoW install CDs and so far so good... I'm patching

---

### Post by hyper_ch on 2007-12-10
instead of just using
```

ls

```
you can also use
```

ls -al

```
--> then you'll get all files/folders
and if it's too big to fit on one screen:
```

ls -al > ~/Desktop/output.txt

```
That will create an output.txt file on your Desktop with all the files/folders

---

### Post by geirha on 2007-12-10
It's probably an ISO9660/HFS+ hybrid. Meaning that it contains files for both windows(ISO9660) and Mac (HFS+). The HFS+ extention may hide files on the CD, they will not be visible even with ls -la. Ubuntu probably detects the HFS extention and mounts it with that one automatically. If you mount it as a regular iso9660 cd it should look like it does in windows. 

Type ```
mount
``` which should display all mounted filesystems. The filesystem mounted last is usually the last line. It probably says something like ```
[COLOR="Blue"]/dev/hdc[/COLOR] on [COLOR="Green"]/media/cdrom0[/COLOR] type hfs (ro,....
```

Unmount it manually, and then mount it manually with iso9660:
```
umount [COLOR="Green"]/media/cdrom0[/COLOR]
sudo mount -t iso9660 [COLOR="Blue"]/dev/hdc[/COLOR] [COLOR="Green"]/media/cdrom0[/COLOR]
```

---

### Post by TwistedAx on 2007-12-26
Thank You, You Truely Rox <3

---

