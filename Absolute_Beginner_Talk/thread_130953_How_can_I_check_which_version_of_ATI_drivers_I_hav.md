---
title: "How can I check which version of ATI drivers I have installed?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-15
I'm thinking about looking at changing the drivers I have installed for my 9800 pro. When I move windows around the screen I get trails behind them and it's very annoying :mad: 

I have checked in the Sound and Video forum and I thought the command might be "fglrxinfo" but it just says "command not found". Is there a command to check? Also, is there a way to check from the GUI?

Thanks;)

---

### Post by rfruth on 2006-02-15
"lshw" from the command line (not GUI) displays lots of info, here is my output [http://www.rfruth.net/resume/computers/breezy/breezylshw.txt]("http://www.rfruth.net/resume/computers/breezy/breezylshw.txt")

---

### Post by Clark Nova on 2006-02-15
Ok, I tried that but I can't see anywhere in my file (or yours) which version of ATI's drivers I have currently installed. Am I missing something? Can you see your driver version on your list file? If you tell me what I need to search for using CTRL-F it will help me no end.

Thanks:)

---

### Post by kaamos on 2006-02-15
Try```
locate fglrxinfo
```
Maybe your path is wrong or something.

---

### Post by Clark Nova on 2006-02-15
I followed this guide:

[http://doc.gwos.org/index.php/Install_ATI_driver]("http://doc.gwos.org/index.php/Install_ATI_driver")

and now when I type "fglrxinfo" at the command line I get this:

```
simon@Desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

That can't be right surely, I have a 9800 pro in there. What have I done wrong? Any ideas?:cry:

---

### Post by Clark Nova on 2006-02-15
Ok, I have tried again and followed [this]("http://ubuntuforums.org/showpost.php?p=423584")
 guide I found in the Video and Sound forum. Now I'm getting something more along the lines of what I was expecting:

```
simon@Desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5642 (8.22.5)

```

Except that the grpahic performance seems even worse now. There are still trails behind the windows and now there are often black squares where the window has been, until the screen is redrawn a few seconds later. 

Is this what I should expect? I'm loving playing around with Linux but it's really starting to annoy me when something like this is really easy in Windows. The same  graphics card in Windows XP gives me no trouble at all, nice smooth movement of windows etc. 

What's wrong? Any suggestions of something else I might try?:-k 

Thanks:KS

---

### Post by kaamos on 2006-02-15
Even though ATIs linux drivers are ****, the card should certainly not perform that badly.

You could try to look for errors in /var/log/Xorg.0.log

---

### Post by Clark Nova on 2006-02-15
[QUOTE=kaamos]Even though ATIs linux drivers are ****, the card should certainly not perform that badly.

You could try to look for errors in /var/log/Xorg.0.log[/QUOTE]

What kind of things should I be looking for in that file? This is all very new to me so please bear with me, I really appreciate your help:KS 

You say the ATI drivers aren't so good, should I think about getting an Nvidia card instead? The 9800pro has served me well for a couple of years now but I only really ever played Star Wars Galaxies gameswise and with that going down the pan as of late I'm not playing much of it. I was thinking I'd just leave the Radeon in there but I really want to get some of the transparancy effects, fades, drop shadows etc working that I was reading about in the customization forum and that guide recommends an Nvidia card too. Perhaps I'll get a new card to go with my new OS, what do you recommend Nvidia wise (if anything)?

---

### Post by Delkster on 2006-02-15
That's right. The proprietary ATI driver is quite slow at 2D, but even then it shouldn't take seconds to redraw a window. By the way, if you don't need 3D acceleration or other such fancy stuff, the X.org ati driver might be better at 2D than ATI's proprietary fglrx driver.

Edit: I didn't necessarily mean that you should get an NVidia card, although their proprietary Linux drivers definitely beat those of ATI. I posted the message saying "That's right" after reading kaamos' post but before seeing yours.

---

### Post by kaamos on 2006-02-15
[QUOTE=SiBuntu]What kind of things should I be looking for in that file? This is all very new to me so please bear with me, I really appreciate your help[/QUOTE]

The log file flags errors with EE and warnings with WW, so you can use the commandline to filter down the amount of visible stuff.

Errors (not good)
```
cat /var/log/Xorg.0.log | grep EE
```
Warnings (some not good)
```
cat /var/log/Xorg.0.log | grep WW
```
Further than that, I don't know what to especially look for. :(

---

### Post by Clark Nova on 2006-02-15
Well, I found a few warnings in there but certainly no errors in the log. Perhaps you are right about the ATI drivers. I have another computer that has an Nvidia card in it (a fanless FX5200 I think it is) so I could always test it out in this machine and see what happens. I can't swap it out permanently though because it's my Media Centre PC and needs to be as quiet as possible.

Is it easy to install the Nvidia drivers in Ubuntu to test and then put my 9800pro back afterwards? Would I need to remove the Nvidia drivers before I put my 9800pro back in do you think?

Thanks again to all who have helped me with this, it's very much appreciated\\:D/

---

