---
title: "WINE - I'm lost of how to use it....."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-06-17
I'm presently dual-booting on my laptop with Ubuntu and WinXP.... but when it comes to my main desktop computer, I want to go all Ubuntu, so I'm trying things on my laptop first so my desktop won't be a trainwreck when I get that far ;)

There is only one Windows program that for me is a 'must-have'.... Adobe Audition 1.5, which is on the compatible list of programs that work with Wine.

It seems that my searches don't turn up a way to install a Windows program in Linux using Wine; of course, it could well be a case of not seeing the forest for the trees :)

I'm using Ubuntu 7.04, have the latest version of Wine and have the Adobe installation cd.... what do I do now??

Thanks! :D

---

### Post by floke on 2007-06-17
Put CD in
open with Wine File
Open D drive
Click on install.exe or whatever it is
Install
Go to C drive
Click on runmyprogram.exe or whatever it is

All done

---

### Post by Cappy on 2007-06-17
Open the installation CD, double click on the install.exe or whatever the setup program is. If that doesn't work, right click on the install instead and select "Open with" and select or type "wine"

---

### Post by Motoxrdude on 2007-06-17
Go to where you cd is. Right click on the setup.exe or autorun.exe, select 'Open with other application'>>Use custom command and type wine. Press ok and it should work.

---

### Post by ElEdwards on 2007-06-17
OK, I tried that but it didn't work. :(

I put the cd in and got a window showing me the files on it.  I did a right-click on "setup.exe", selected "Open with 'wine'" and received several errors, one after the other, which are below.

I tried double-clicking on "setup.exe", too... but got the same results.

Thoughts? :(

---

### Post by Cappy on 2007-06-17
Try
```

wineprefixcreate
env WINEPREFIX="/home/${USER}/.wine" wine "/media/cdrom/setup.exe"

```

Check to make sure your cdrom is actually /media/cdrom/ (It is at the top of nautilus [file browser] when you insert the CD)

You may also want to run
```
winecfg
``` and look under the drives tab to make sure the correct path to your cdrom is set there.

---

### Post by ElEdwards on 2007-06-17
AH!!  Got it!  I feel dumb now.....

The "Setup.exe" I was trying to work with is the "Main Menu" of the CD, which presents things like:
- Install this program
- view the Read Me file
....etc.

I went a little deeper in the CD and found a directory for the program (Adobe Audition) and in that directory was *another* "Setup.exe" that is for the program itself. :)

I went through the steps outlined in previous posts to this thread and I have now Audition working!!

Thanks! :D

---

