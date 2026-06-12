---
title: "Screen saver freeze"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by brant3 on 2007-08-12
Just installed Ubuntu today.
Was going through the screen saver options--
clicked on molocule--the whole system froze--
nothing works at all.
had to shut dowm with power button.
Now everything works BUT when I try to change to new screen saver,
the whole thing freezes again OR if I let the computer sit for 10 minutes,
(which is what set in screen saver) when the screen saver comes on--
the whole thing freezes again! 
I can't get to the settings to change anything--once I'm there, it freezes.
HELP!

---

### Post by panther_sn on 2007-08-12
Is it just with molecule or others as well?

It might be your video card, What video card are you running?

---

### Post by Arthur Archnix on 2007-08-12
Try this, in a terminal
```
sudo gconf-editor
```
Browse to /apps/gnome-screensaver/

and change mode to "blank-only"

Quit, then restart x with Ctrl Alt Backspace

---

### Post by koolkatkiwi on 2007-08-12
> **brant3 said:**
> Just installed Ubuntu today.
Was going through the screen saver options--
clicked on molocule--the whole system froze--
nothing works at all.
had to shut dowm with power button.
HELP!

I've had exactly the same problem, except that some of the screen savers work. When I was scrolling through to try different ones, two (on two separate occasions, after a re-boot) caused the freeze. There may be others that do that, but I wasn't game to try each one and do a re-boot each time.

I ended up just clicking on the "blank screen" option, which doesn't cause a freeze.

My system has quite poor specs. I wonder if yours does too, and that is the problem?

Cheers,
Kath.

---

### Post by inchaos on 2007-08-13
I'm having the same exact problem and I just opened my brand new Dell Inspiron 1420 today that came with Feisty on it.

I get a blank screen with a cursor and an occasional flicker.

I can't even select other options to see if different screensavers work.  I can't select blank screen.

ARGH!

Brand new computers should WORK.

---

### Post by jmnormand on 2007-08-13
the problem with the 1420 is the graphics driver.  if your running intel graphics see this thread [http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408) and try changing out your graphics driver.  this will fix your problem. i do not however know the current state of the nvida graphics.

---

### Post by inchaos on 2007-08-14
That's what I assumed, however the driver the how-to reccomends is for a different graphics card than I have.  
I have an Intel Media Graphics Accelerator 3100, chipset is G33 I believe.  

The reccomended package says it is for 9xx and 8xx chipsets.  

Soo...I dunno?  I can live without a screensaver, so far it hasn't affected anything else.

I'm kind of new to Ubuntu, so maybe I don't know quite what I'm talking about anyway :)

---

### Post by pdxken on 2007-08-15
Hi Folks. I am new to this stuff but am having fun and frustration.

I had a problem similar to this. I was trying all the cool screensavers. When I got to molecules the computer froze up. After trying everything else finally had to pull the plug to reboot. If I tried to change the screensaver the computer would imediately freese up. PITA!

After countless hours and half a bottle of Scotch and reading this thread I found a file called
%gconf.xml in /home/ken/.gconf/apps/gnome-screensaver.
It had a line something like
<stringvalue>screensavers-molecules</stringvalue>.
I edited molecules to none to change the line to line
<stringvalue>screensavers-none</stringvalue>

At this point I rebooted just to be safe and was able to then open System > Preferences > Screensaver on the desktop and change the screensaver to one that worked OK before.

It seems to work fine now. I just won't use the molecules screensaver any more.

Thanks. Ken.

---

### Post by natehall on 2007-10-31
Brand new Dell Inspiron 1420 right out of the box and the screen saver option freezes . Called Dell and they had nobody that could help! I downloaded all the updates and it fixed the freeze problem only to make the browser freeze up! After rebooting the whole system from BIOS I found out a few of the screen savers do work.  You can go to Applications, Accessories, Terminal, type in conf-editor ,browse to apps , then gnome-screen saver,   and change mode from single to blank-only.  Close the editor, then Ctrl Alt  Backspace to restart the computer. You can pick out a screen saver from there. I know the anything with “ant” in freezes , and so does the skyrocket one, which is too bad because it was pretty neat.

---

### Post by inchaos on 2007-11-01
Yeah, same thing with mine after I bought it except that I had serious crashes whenever I tried to use the non-functional screen savers.  A kernel update after a few weeks fixed the problem.

Now I've upgraded to Gutsy and I've got almost the same problem over again with non-functioning screensavers.  I havn't played around to see if it causes the same crashes because I'm not feeling particularly violent toward my HDD.

---

### Post by HDave on 2008-01-03
This issue is now a confirmed bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103400]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103400")

---

