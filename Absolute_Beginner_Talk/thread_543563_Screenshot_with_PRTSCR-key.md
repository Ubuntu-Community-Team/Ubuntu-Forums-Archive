---
title: "Screenshot with PRTSCR-key?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-09-05
I have read about a gazillion times that it's possible to take a screenshot by simply hitting the "print screen" key.  I have never worked out how to actually do this though.  After I hit the key there isn't an image in the clipboard which I could then paste into, say, an Abiword document.
So what am I doing wrong, and how do I do it right? :confused:
NB I'm aware of the "take screenshot" utility from gnome-utils, but I'm curious how to put this fabled PRTSCR-key to work, thanks.

---

### Post by jvc26 on 2007-09-05
Admittedly I am currently using Gutsy, but I am pretty sure that the same was true of Feisty, hitting PRTSCN throws up a 'save image' dialogue into which I put the name and location I want to save it and it does so. - Is this not the case therefore for you? Once its saved you can then insert it via 'insert image' from file as per usual word/office apps.
Il

---

### Post by Blofeld on 2007-09-05
Aye!  There's the rub!
No, I don't get this "save image" dialogue, therefore I presume that the print-screen-shenanigan hasn't been implemented here in Xubuntu.
OK, fine, good to know, so I'll just use gnome-utils instead.
Many thanks for the info, Illu. :KS

---

### Post by Tautoa on 2007-09-05
My prtscr key didn't work properly either (in Kubuntu Feisty), but it did work after playing with the keyboard shortcuts options. I've never tried Xubuntu, but I assume it has a way of defining keyboard shortcuts too? Try assigning the key to the 'take a screenshot' option?

---

### Post by asmoore82 on 2007-09-05
> **Blofeld said:**
> I have read about a gazillion times that it's possible to take a screenshot by simply hitting the "print screen" key.  I have never worked out how to actually do this though.  After I hit the key there isn't an image in the clipboard which I could then paste into, say, an Abiword document.
So what am I doing wrong, and how do I do it right? :confused:
NB I'm aware of the "take screenshot" utility from gnome-utils, but I'm curious how to put this fabled PRTSCR-key to work, thanks.

the print screen key works out-of-the-box on Ubuntu with Gnome ...

you should be able to install the package and configure your keyboard shortcuts to work the same way ... I think ...

```
**asmoore@asmoore-laptop:~$** which gnome-screenshot 
/usr/bin/gnome-screenshot
**asmoore@asmoore-laptop:~$** dpkg -S /usr/bin/gnome-screenshot
gnome-utils: /usr/bin/gnome-screenshot
```

the command is 'gnome-screenshot' and provided by the 'gnome-utils' apt package.

---

### Post by Sammm_ on 2007-09-05
What I did was install scrot (sudo apt-get install scrot) and then just mapped the "scrot" command to the PrtScrn button.

---

### Post by Steveway on 2007-09-05
Thanks for the info with scrot.
It works also in XFCE, I just needed to add: scrot /home/steveway/
And press the print-key.
Only the command scrot didn't work, it works in the terminal but not if I assign it to the print-key, scrot /home/steveway/ however works.
Thanks.

---

### Post by kerry_s on 2007-09-05
> **Sammm_ said:**
> What I did was install scrot (sudo apt-get install scrot) and then just mapped the "scrot" command to the PrtScrn button.

that's what i use to.

---

### Post by Nythain on 2007-09-05
yeah, outside of gnome and kde scrot is your friend... very usefull in xfce and fluxbox

---

### Post by Blofeld on 2007-09-06
With a little help from my friends in this thread I figured out how to have a screenshot taken and conveniently deposited on my desktop when I hit PrtScr with Xubuntu 7.04.
First, install scrot by running ```
sudo apt-get install scrot
```
Secondly, go to Xfce Menu > Settings > Keyboard > Shortcuts and add this line, add a new scheme (name it after yourself), add a shortcut, and enter ```
scrot '%T.png' -e 'mv $f ~/Desktop/'
```
When the "set shortcut" window opens hit the PrtScr key, close the window, and voilà, you're all set, instant party on your desktop.
:guitar:
Note:  the scrot command means:  "save the screenshot with a timecode (scrot always uses the current directory for this), then do another thing (-e = execute) and move (mv) that file ($f) to ~/Desktop".
Note 2:  the scrot manual is [here]("http://fresh.t-systems-sfr.com/unix/src/privat2/scrot-0.8.tar.gz:a/scrot-0.8/scrot.1").
Thanks for the fruitful input in this thread, everyone.

---

### Post by RedSquirrel on 2007-09-07
I use imagemagick:

```
sudo apt-get install imagemagick
```

After it is installed:
```
import -help
```will give the options you can use.

Here are the keyboard shortcuts I use in Fluxbox:

The whole screen:
```
Print :Exec import -pause 5 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg

```Click on a window or click & drag to select a portion of the screen:
```
Mod1 Sys_Req :Exec import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg

```

---

### Post by wickstopher on 2007-09-12
I can't figure out a way in Kubuntu to take a window shot.  Back when I was using gnome, it was alt-printscreen, but that doesn't seem to work in Kubuntu,  I found and edited the shortcut under System Settings > Keyboard & Mouse > Keyboard Shortcuts, but it still doesn't work with the custom shortcut I enabled.

---

