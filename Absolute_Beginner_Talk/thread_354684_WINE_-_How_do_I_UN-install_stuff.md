---
title: "WINE - How do I UN-install stuff?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-06
Hi...  I've just been playing around with Wine. I managed to get my only 'cannot do without' Windows program to install, but nothing I can do will get it to run.

So, how do I get it off my Ubuntu system?  Is it OK to just go into the .wine directory and delete the program folder there, or is it more complicated (or more easy!) than that?

Thanks!

---

### Post by jethro10 on 2007-02-06
Dunno if there is any proper way to do it, but I do as you are suggesting and it's fine.

Or has been for the 12 months i've been on Linux (this month!)

Jeff

---

### Post by pizzutz on 2007-02-06
What application were you trying to run?

---

### Post by Brunellus on 2007-02-06
simple remove the relevant directory in ~/.wine/drive_c/

Simple!

---

### Post by whitefort on 2007-02-06
Thanks, Jethro.

Pizzutz, the program was Poser 6.  It's supposed to work (sort of) in Wine, but I just couldn't get it going.  I'm going to drop back a couple of versions and try Poser 4 and see what happens.

---

### Post by Cannaregio on 2007-05-27
> **whitefort said:**
> Thanks, Jethro.

Pizzutz, the program was Poser 6.  It's supposed to work (sort of) in Wine, but I just couldn't get it going.  I'm going to drop back a couple of versions and try Poser 4 and see what happens.

Well I would be interested in your experiences, but I see you never published back.
I get an 'out of memory' error with poser 4

These are my specs:
2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
wine-0.9.37
and I have 3 giga of RAM

---

### Post by whitefort on 2007-05-27
> **Cannaregio said:**
> Well I would be interested in your experiences, but I see you never published back.


To be honest, I just gave up on Wine. I've now tried all my Windows programs (of all sorts, ranging from graphic-intensive to simple text-based stuff), and I couldn't get a single one of them to work.  There was a post recently where someone got Poser 6 working, apparently well enough to use - but I haven't been able to repeat their success.

I still need Poser, so it means I have to keep one of my machines running windows. Bummer.

In the meantime, I'm trying hard to learn to use Blender.  It's not really a Poser substitute, being much more complex than I actually need.  I can sit down and produce a picture or animation in hours using Poser - with Blender, I suspect the same process would take weeks or months using Blender, as I'd need to model, rig, and texture everything from scratch (instead of just using pre-existing models, as with Poser).

Still I'm prepared to give it a shot. I would really like to be totally free of windows.

Anyway, to get back to the topic, no, I had no success with wine whatsoever - I hope you have better luck!

---

### Post by Brunellus on 2007-05-29
> **whitefort said:**
> To be honest, I just gave up on Wine. I've now tried all my Windows programs (of all sorts, ranging from graphic-intensive to simple text-based stuff), and I couldn't get a single one of them to work.  There was a post recently where someone got Poser 6 working, apparently well enough to use - but I haven't been able to repeat their success.

I still need Poser, so it means I have to keep one of my machines running windows. Bummer.

In the meantime, I'm trying hard to learn to use Blender.  It's not really a Poser substitute, being much more complex than I actually need.  I can sit down and produce a picture or animation in hours using Poser - with Blender, I suspect the same process would take weeks or months using Blender, as I'd need to model, rig, and texture everything from scratch (instead of just using pre-existing models, as with Poser).

Still I'm prepared to give it a shot. I would really like to be totally free of windows.

Anyway, to get back to the topic, no, I had no success with wine whatsoever - I hope you have better luck!
Generally, I advise people to treat WINE as a last resort.  Do not assume that your applications will run on WINE.  Rather, ask yourself:

1) Do I need this application?

2) Is there a Linux-native alternative?

3) Can I live with the alternative instead?

If you can't, then you try WINE as a last resort.

---

### Post by cwmoser on 2007-05-29
I use wine for eSword and some other applications.

Major applications like Quicken and Quickbooks, I use Crossover.

Other applications that are .NET v1.1 compliant, I use mono - ex:  ProShow.

As far as uninstall, I guess the only way is to use the applications uninstall utility if there is one.

Carl

---

### Post by Cannaregio on 2007-09-15
> **whitefort said:**
> To be honest, I just gave up on Wine. I've now tried all my Windows programs (of all sorts, ranging from graphic-intensive to simple text-based stuff), and I couldn't get a single one of them to work.  There was a post recently where someone got Poser 6 working, apparently well enough to use - but I haven't been able to repeat their success.

I still need Poser, so it means I have to keep one of my machines running windows. Bummer.

In the meantime, I'm trying hard to learn to use Blender.  It's not really a Poser substitute, being much more complex than I actually need.  I can sit down and produce a picture or animation in hours using Poser - with Blender, I suspect the same process would take weeks or months using Blender, as I'd need to model, rig, and texture everything from scratch (instead of just using pre-existing models, as with Poser).

Still I'm prepared to give it a shot. I would really like to be totally free of windows.

Anyway, to get back to the topic, no, I had no success with wine whatsoever - I hope you have better luck!


I managed finally to run Poser 6 in wine. Uff.

Important steps:
Copy some dlls into wine's system 32: msvcp60.dll, msvcirt.dll, and whatever else wine is asking for 

Always run ```
wine Poser.exe
``` from inside wine's  own poser 6 directory, so that you can see all error messages

Alternatively use the more verbose 
```
WINEDEBUG=warn+all wine poser.exe
```

Previously run winecfg and chose "graphic-->emulate a virtual desktop --> 1024*768" (say)

Now I have Poser 6 up and running

Launcher is 

```
env WINEPREFIX="/home/father/.wine" wine "C:\Program Files\Curious Labs\Poser 6\Poser.exe"
```

Rendering is perfect, but some complex figures seem to be missing some parts while pre-viewing inside Poser before rendering. I wonder why.

---

### Post by lisati on 2007-09-15
My system has a "Wine software uninstaller" option in the Applications->System tools menu. I'm surprised I didn't notice a reference to it......

---

### Post by coolen on 2007-09-15
The proper way to remove programs is with the wine uninstaller (the command is simply uninstaller).
Brings up a window, select the program, and remove it.
It might not always work, though. MSN wouldn't go away when I used this method, and other programs weren't in the list.

---

### Post by Cannaregio on 2007-09-24
Got Poser 7 up and running.
Same procedure I used for Poser 6 (see above).
There's only one problem, while the rendering times are much quicker than in windows, the pre-rendering figures, in the 'pose' room, have some transparent missing parts (a cheek, a shoulder, that kind of missing parts). This is strange and annoying, and I wonder if someone could point me to a solution I could use.
The fantastic blitz-rendering times are still worth posing even with these annoying missing parts, but I would like my poser to be perfect also in the pre-rendering rooms. Anyone can help?

---

### Post by Cannaregio on 2007-10-05
Solved upgrading the NVIDIA drivers to 100.14.19 (both nvidia proprietary and glx) during my upgrade to Gutsy (beta).
Now I have ultraquick rendering and ultraquick posing as well :)

---

### Post by por100pre1 on 2007-10-05
For uninstalling programs installed with WINE:

```
uninstaller
```

---

