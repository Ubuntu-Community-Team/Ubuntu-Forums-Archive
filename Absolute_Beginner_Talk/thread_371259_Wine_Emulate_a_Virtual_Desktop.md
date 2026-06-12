---
title: "Wine Emulate a Virtual Desktop"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by dfreer on 2007-02-26
Ok, this probably sounds like a basic question, but I've tried google, ubuntuforums search, and winehq... 

I am currently running wine 9.31 on Edgy AMD64. I have several programs installed through wine, including Steam. I want to be able to run Steam in a virtual desktop, but I DON'T want to run the rest of the programs in the virtual desktop... having to go through winecfg each time to enable/disable the virtual desktop is really annoying. 

My question: is there a way to pass an argument to wine so that when I start Steam and only steam it will run in a virtual desktop? For example:

winecfg --> Emulate Virtual Desktop = OFF
```
wine "C:\Program Files\Steam\steam.exe" --emulate-virtual-desktop 1024x768
```

---

### Post by hansonry on 2007-03-01
Good question I too have some games that need to have an Emulated Desktop and some that dont. I have done some searching my self, no luck tho. 

I heard that the next versions of wine would take care of that, but I am intrested in hearing if anyone else has a solution.

---

### Post by dfreer on 2007-03-02
bump :D

---

### Post by Dylnuge on 2007-03-05
Yes, you can do this.

Open winecfg. Click Applications Tab if not selected by default. If the application you want is in the list, click it. If not, click add application and browse for it. Now select the application. Click the Graphics Tab. Choose Emulate a virtual desktop. Enter the size for the virtual desktop. Click OK. Remember to click All Applications if you need to change any global settings after this.

---

### Post by dfreer on 2007-03-05
Thanks a bunch! I saw that you could change which windows version to use, but I didn't realize that if you select an application and then switch tabs that it configured only that application... i thought the other tabs were global settings... Thanks again!

---

### Post by moabi on 2007-03-13
This si very useful information. However, on my computer, the 'emulate a virtual desktop' checkbox is greyed out when I have selected an individual application. Any idea why?

thanks
M.

---

### Post by Onurzaim on 2007-03-13
Do you have the chance to try cedega?

---

### Post by Nikusan on 2007-07-04
> **moabi said:**
> This si very useful information. However, on my computer, the 'emulate a virtual desktop' checkbox is greyed out when I have selected an individual application. Any idea why?

thanks
M.

Same problem here. Wine 0.9.40 from winehq. Any ideas?

---

### Post by mikerobinson on 2007-07-23
bump... i'm having the same problem 0.9.41

---

### Post by Endolith on 2007-09-19
> **moabi said:**
> This si very useful information. However, on my computer, the 'emulate a virtual desktop' checkbox is greyed out when I have selected an individual application. Any idea why?

Same here.

---

### Post by Cannaregio on 2007-10-07
> **moabi said:**
> This si very useful information. However, on my computer, the 'emulate a virtual desktop' checkbox is greyed out when I have selected an individual application. Any idea why?

thanks
M.

Same problem here, but only with SOME applications (not all).
Using ubuntu Gutsy, Nvidia last drivers and wine 0.9.46
I think this might be due to older applications that do not have a bigger resolution (winSPMBT and winSPWW2 for instance).

On the[ publisher's site]("http://linetap.com/www/drg/SPCamo-4.htm"):
```
Game size is no longer restricted to merely 640 by 480 pixels. User can choose from 640x480, 800x600, and in the enhanced CD version 1024x768, 1152x864, 1280x1024 and 1600x1200 modes.
```

And since noone has the enhanced CD version, we (and wine) are limited to 640*480 and/or 800*600.

Could this be the (simple) explanation?

---

### Post by AxAeo on 2007-12-08
Same problem with the greyed out things... Anybody know how to fix?

---

### Post by GuySmily on 2007-12-29
I just spent the last 3 hours trying to figure out how to run stuff in windowed mode... And it's actually simple.  From a terminal:
```
wine explorer /desktop=MyDesktopName,1024x768 /path/program.exe
```

It may have taken 10 months, but at least this thread has an answer now..

---

### Post by ekravche on 2008-03-15
> **GuySmily said:**
> I just spent the last 3 hours trying to figure out how to run stuff in windowed mode... And it's actually simple.  From a terminal:
```
wine explorer /desktop=MyDesktopName,1024x768 /path/program.exe
```

It may have taken 10 months, but at least this thread has an answer now..

Thanx that worked for me

---

### Post by Psyphre on 2008-03-29
wine explorer /desktop=MyDesktopName,1024x768 /path/program.exe

What does the desktop part mean? I dont know what to put for that part.

---

### Post by captinkid on 2008-04-22
Works Great!

Right click on an existing wine shortcut

Go to properties

Go to launcher

You will see a line like the one below:

env WINEPREFIX="/home/yourhomedirectory/.wine" wine "C:\Sierra\Half-Life\hl.exe"

Then copy the text below:

explorer /desktop=MyDesktopName,1024x768 

Between wine and the program

Like so

env WINEPREFIX="/home/yourhomedirectory/.wine" wine explorer /desktop=MyDesktopName,1024x768 "C:\Sierra\Half-Life\hl.exe"

And then just set the 1024x768 to whatever you want the window size to be 800x600, 1280x1024, etc.

MydesktopName just sets the name for the virtual desktop

Half life works great but it needs to be in a window for the menu to work right.

---

