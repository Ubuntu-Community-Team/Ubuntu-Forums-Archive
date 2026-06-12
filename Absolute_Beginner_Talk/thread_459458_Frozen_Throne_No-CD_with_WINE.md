---
title: "Frozen Throne No-CD with WINE?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-30
My question is simple, how can I get Frozen Throne to work without the CD? Do I need to make a virtual image or something?

---

### Post by zorkerz on 2007-08-18
Im looking for the same thing. My x61 only has a cd drive with the docking bay and Id rather not need that for warcraft. I starting to see if I can mess around and get warcraft to work today.

---

### Post by olejorgen on 2007-08-18
I have not gotten any of the no-cd images around to work. Currently I'm using a crack. If you promise that you *own* the game I'll send it to you.

---

### Post by zorkerz on 2007-08-18
mine works with the nocd i have used in windows unfortunately i do not know which one this is. I am running Frozen Throne v1.21 
I probably got my no cd crack from megagames.com or gamecopyworld.com
good luck

---

### Post by TheN0ble on 2007-09-04
Hey, im trying the same thing. I have an idea. When you try to use the NO-CD crack, you get the error:  ERROR 1: Could not find Warcraft III directory. Im guessing the problem is Its trying to find the regular windows path and not wines, so you think there is a way to edit/hexedit/config the Install.exe (No-CD Crack File) to direct the path to the wine path??? Any ideas???

---

### Post by cogadh on 2007-09-04
The Wine path is a regular Windows path. As far as the executable is concerned, it is sitting in "C:\Program Files\Game\Directory". One of the basic functions of Wine is to do that.

A couple of stupid questions: did you place your cracked .exe in the Warcraft III directory and are you cd-ing to that directory before you try to run it?

---

### Post by TheN0ble on 2007-09-10
Yes, the CD crack loads perfect, but when you try to run the program, I get a error, invalid warcraft directory, so the Crack can't find the warcraft directory. I was wondering If there are any CD image mounting software for ubutu/wine to mount a frozen throne cd image to see if that works?

---

### Post by olejorgen on 2007-09-10
There are (search for "iso mount linux" or "cdemu"). The problem is that Warcraft uses securerom or somthing, and to my knowledge there is no emulator for linux (?)

---

### Post by cogadh on 2007-09-10
Actually, the SecuRom copy protection on Warcraft works perfectly in Wine (as do many SecuRom protected games), you just need to have your CD drive configured correctly. In winecfg, you need to make sure that your CD-ROM is correctly set up as drive type "CD-ROM" and you also probably need to create a device symlink to the /dev entry for the drive in Wine's dosdevices directory. Technically, you shouldn't need to use a crack for Warcraft or any of the expansion packs.

---

### Post by olejorgen on 2007-09-10
And this should work with mounted isoes too? I'm quite sure I've tried that, but maybe something have happend in between.

---

### Post by cogadh on 2007-09-10
As long as the mount directory for the ISO is set up as a CD-ROM type drive in winecfg, I believe it should work. However, I can only say it will work for certain with an actual CD and drive.

---

### Post by TheN0ble on 2007-09-11
Ok, i configured wine so I have a CD-ROM device, i put as d: , so now i have a /drive_d and /dosdevices/d: folder, I tried to mount the frozen throne iso image to both folders and had no luck with either one, and tried to run the autoplay.exe and frozen throne.exe and still no luck, every time it says "no cd detected", what would be the correct way to mount the ISO with wine? i was doing this:

cd /home/myname/.wine/drive_c/Program Files/Warcraft III
sudo mount -o loop war3.iso /home/myname/.wine/drive_d
and i tried
sudo mount -o loop war3.iso /home/myname/.wine/dosdevices/d:

wine autoplay.exe
and i tried from the wine warcraft folder
wine frozen throne.exe

Any more ideas? Thankx!

---

### Post by jetpeach on 2008-01-28
i too am looking for a solution. i own frozen throne but hate having to put in the CD! any help is appreciated.

---

### Post by derred on 2008-01-28
does this help?
[http://www.gameburnworld.com/gp/gamefixes/warcraft3thefrozenthrone.shtml](http://www.gameburnworld.com/gp/gamefixes/warcraft3thefrozenthrone.shtml)

It's common to need a crack to run games under wine since wine doesn't support all the copy protection schemes and it doesn't treat the cdrom drive as a drive (like in windows) but more like a directory(like in linux) so it doesn't "see" all the hidden data on the disk.

---

### Post by Echow on 2008-01-28
Just keep in mind that if you use a crack it may not work if you run warcraft with```
wine /path/to/warcraft/war3crack.exe -opengl
```
You will probably need to write a script which goes into the folder first before running the crack eg:
```
cd /path/to/warcraft/
wine war3crack.exe -opengl
```

Ed

---

### Post by derred on 2008-01-28
> **Echow said:**
> Just keep in mind that if you use a crack it may not work if you run warcraft with```
wine /path/to/warcraft/war3crack.exe -opengl
```
You will probably need to write a script which goes into the folder first before running the crack eg:
```
cd /path/to/warcraft/
wine war3crack.exe -opengl
```

Ed

Good idea Ed. I just replaced the original with the no/cd patch so when I used the shortcut on the desktop created by wine it automaticaly gave the correct arguments

```
[Desktop Entry]
Name=Microsoft Reader
Exec=env WINEPREFIX="/home/derred/.wine/" wine "C:\\Program Files\\Warcraft III\\War3.exe" 
Type=Application
StartupWMClass=Wine

```

Might be somewhat inaccurate since I don't have it installed anymore (trying to install C&C generals and only have a 30 gb hard disk on my laptop)

---

### Post by running_wild on 2008-01-29
Try this:
[http://w14.easy-share.com/13786501.html]("http://w14.easy-share.com/13786501.html")
Is a pach to the version 1.21a runs whit no cd and you can play in battelnet on the eurobattle server.
Enjoy.

---

