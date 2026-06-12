---
title: "Wine doesn't show correct disk space"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by skroops on 2008-01-22
I've been trying to install Fallout 1 with wine. Problem is that the installer shows only 180MB free space. I have way more than that free on the drive. The wine c_drive is located at /home/skroops/.wine. I have 39GB of free space on my /home partition, what gives

---

### Post by TeaSwigger on 2008-01-22
Good question. During installation, where do you specifiy it should put the files?

---

### Post by A4006 on 2008-01-22
Wine uses a virtual C:/ drive that mimics windows.  It doesn't use your whole HDD for storage.  I've had this problem before, when I didn't make the Ubuntu partition big enough, and Wine just used up a certain percentage of the partition, about 1 gig.  I just gave up on it, you might want to look on their site [http://www.winehq.org/]("http://www.winehq.org/") for more info.

---

### Post by TeaSwigger on 2008-01-24
skroops, perhaps try "mapping a drive" in WINE just for installing the games to? If you don't know, you'd open WINE configuration, in a terminal that's just

```
winecfg
```

and hit the devices tab. You'll see hunting around there how to add a new "drive" (this only affects WINE). Pick a drive letter, point it to where you want the stuff like /home/Y-O-U/games could be G: or whatever. When you install the game or program, tell the installer to use that location. Can't hurt to try. 

WINE is doing an incredibly complex task, it's amazing this stuff ever works.

---

