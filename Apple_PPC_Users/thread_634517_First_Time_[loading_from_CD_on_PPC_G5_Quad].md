---
title: "First Time [loading from CD on PPC G5 Quad]"
date: 2007-12-07
forum: Apple PPC Users
---

### Post by Kenatron on 2007-12-07
Ok. I need help loading Ubuntu 7.10 from a DVD I made. I know I don’t need a DVD but I have no more CDs. I downloaded Gusty Gibbon  [7.10] from [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/). I chose the version that says you can download from a CD. I used Toast Titanium to make the DVD from the ISO/DMG file. I put the DVD in and it asks me something along the lines of loading the OS on a command prompt like black screen. I typed y for yes... said error loading something... so I read it and it said default something was "live" so I typed in live and pressed enter. Something loaded successfully and then the screen went blank I waited for like a minute and then manually restarted my computer. What should I do? Wait longer, did I make a mistake. I’m so brand spanking new it hurts and I really want to try Ubuntu.

---

### Post by Auria on 2007-12-07
I am not sure if this info applies to you but look at :
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

7.10 for PPC has some important bugs in. You can either look around for information about how to fix these problems, you can also try 7.04 if you're don't feel like getting your feet wet too much :)

---

### Post by Kenatron on 2007-12-08
OK so I looked at that and tried several things but I think that it was done wrong. Tried again and typed modprobe ide-core [enter] exit [enter] at the black screen. Nothing works but I turned my speakers on and I hear a little tune after around 40 seconds and the CD drive sounds busy. Then everything stop and nothing happens. I pressed control apple f2 or something and another blank screen came up. Another command driven [dos-like] black screen. I typed modprobe ide-core again and that did nothing. It said something about using sudo commands. I'm totally lost so if some one knows how to fix this please tell me. Btw thanks for the info.

---

### Post by stmiller on 2007-12-08
Type live-powerpc64 at the boot prompt, or install-powerpc64 (which ever it says).

The G5 requires a 64bit kernel. I could never get a live CD to work with my dual 2.0Ghz G5. I always used the alternative CD to install. No pretty desktop, but same installer.

---

### Post by 3rdalbum on 2007-12-10
> **Kenatron said:**
> I pressed control apple f2 or something and another blank screen came up. Another command driven [dos-like] black screen. I typed modprobe ide-core again and that did nothing. It said something about using sudo commands. I'm totally lost so if some one knows how to fix this please tell me. Btw thanks for the info.

Control-Option-F2.

The command should be:

```
sudo modprobe ide-core
```

(the "sudo" thing before the command tells Ubuntu that you want to run the command as administrator - since you're basically adding parts to the core of the system while it's running, only the administrator is allowed to do it! The administrator is also known as "root".)

---

