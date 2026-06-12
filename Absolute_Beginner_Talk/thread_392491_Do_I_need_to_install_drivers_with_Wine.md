---
title: "Do I need to install drivers with Wine?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-24
I installed Warcraft 3 with Wine but when I try to play it lags really bad, even in the menu.  I tried to adjust the settings but that didnt help at all.  I was wondering if I needed to install the drivers for my video card with Wine in order for it to work.

---

### Post by camz on 2007-03-24
Not sure about the drivers but you could check your connection speed.

---

### Post by eljalill on 2007-03-24
I don't think you need to install the dirvers (again).
But since wine kind of "translates" between your your OS and the game, it makes things slower (also every emulator does). Just additional calculating space required there.

But anything you should need to know about this,
you might find here
[http://appdb.winehq.org/appbrowse.php?iCatId=2](http://appdb.winehq.org/appbrowse.php?iCatId=2) .

---

### Post by YokoZar on 2007-03-25
> **eljalill said:**
> I don't think you need to install the dirvers (again).
But since wine kind of "translates" between your your OS and the game, it makes things slower (also every emulator does). Just additional calculating space required there.

But anything you should need to know about this,
you might find here
[http://appdb.winehq.org/appbrowse.php?iCatId=2](http://appdb.winehq.org/appbrowse.php?iCatId=2) .This is incorrect - Wine is not an emulator.  Your program is running directly via Wine in the same way that any other program is running (say, Gaim running under the GTK API)


Running the executable for Windows drivers with Wine will not work under Linux, as Windows drivers are not designed for the Windows kernel.  Wine is for applications only - you'll need Linux drivers for your hardware.

---

### Post by eljalill on 2007-03-25
I know that wine is not an emulator, and I didn't stricly speaking say that...
But is it not true, that if you run a program in a program, (which you are doing in wine), the "outer" program has to "translate" between OS and inner program, which would alsways make thing slower? Just with many applications you wouldn't notice, because you have CPU space available...?

If not, how does wine work?
(sorry don't mean to hijack thread or so... but maybe this is also interesting for the threat starter)

---

### Post by Hevoos on 2007-03-25
Are you sure you run it with the -opengl flag? In a terminal type 'wine /path/to/game.exe -opengl'. If you don't type the opengl thing the game will be *really* slow. ;)

---

### Post by david_kt on 2007-03-25
> **Brucey said:**
> I installed Warcraft 3 with Wine but when I try to play it lags really bad, even in the menu.  I tried to adjust the settings but that didnt help at all.  I was wondering if I needed to install the drivers for my video card with Wine in order for it to work.

First of all, see whether you have a direct rendering. For example, ATI is detected correctly and the appropriate driver is installed, but normally there is no direct rendering which will cause lag. To check direct rendering, type in terminal (or copy and paste below command):

[INDENT]glxinfo | grep render[/INDENT]

See what the output.

DK

---

### Post by Lord Illidan on 2007-03-25
Only one piece of information here is correct, the ```
wine war3.exe -opengl

```
Make sure you navigate to the file with the terminal and type in that code.

This may help : [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

