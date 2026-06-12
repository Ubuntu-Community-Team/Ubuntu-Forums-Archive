---
title: "Screensaver freezes system"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by A*p on 2007-06-20
I installed Feisty onto my sisters computer but it has the problem that when the screensaver starts it freezes the system.  The only was to power the system down is to pull the plug!!  This bug has been reported in the forums before with a solution but that solution no longer works... here is the other thread... [http://ubuntuforums.org/showthread.php?t=406267](http://ubuntuforums.org/showthread.php?t=406267) 

The solution is to change the .xscreensaver file and disable the screensaver that is causing the problem, but I have not been able to locate this in feisty, so I cannot apply the fix.  Does anyone know where the equivalent file is so that the molecule screensaver can be disabled.

---

### Post by diatribe on 2007-06-20
if you go to system->preferences and select screensaver, you can set which one you want to use; just pick one that works or select blank screen

---

### Post by A*p on 2007-06-20
Unfortunately I am unable to do that as when you go into the screen preferences, the molecule screensaver displays and freezes the system.

---

### Post by A*p on 2007-06-21
I have fixed it, her system was frozen so I ssh'd into it to reboot, whilst I was there I also made some changes.  Here is how to fix or at least make a work around.

Open your terminal, and from your home directory enter

> gedit .gconf/apps/gnome-screensaver/%gconf.xml

in there you will see the text

> screensavers-molecule

change this to

> screensavers-sonar


save then logout.

You will need to reboot or restart X, one or the other.

Your system should be using the sonar screensaver now.

Please note that I only used the sonar screensaver because it is not 3d and I know it is an installed by default.  You should be able to launch your screensaver prefs now and choose the one you like as long as it is not molecule.

If anybody knows a cleaner way to fix then please post.

---

### Post by the_wasd_man on 2007-06-24
Hey thanks man! I was having exactly the same problem and it was getting pretty frustrating. Your solution worked like a charm. ;)

---

### Post by mummra1 on 2007-06-26
thanks!  I had to do a hard shut down twice b/c of that screen saver.   grrrrr.....

---

### Post by Pink Djinn on 2007-07-02
I had the same problem with the Braid screensaver. I used A*P's method to regain control and it worked a treat. Thanks!

I removed the offending screensaver completely in a terminal (there was only one that caused problems) using:

sudo rm /usr/share/applications/screensavers/Braid

and now I can use the random screensaver option again without it locking up when it reaches Braid.

Just replace Braid in the above with the screensaver you want to remove from the system.

---

### Post by ZxEfR on 2007-07-20
This reply for FYI purposes only......my way allows you to not learn anything......  :(

I had this problem and was able to change the screensaver using the screensaver config GUI.

What I did was to open the config gui.......and since I knew exactly where the gui was going to open on my monitor...do to trying to change the screensaver off of Molecule (or any other screensaver that freezes the system)a couple times.......I just started clicking the mouse where I knew the screensaver list would appear......so I was able to change the screensaver before it activated. It worked the first time I tried it this way......may not always  though.......   :lolflag:

---

### Post by KillerSiafu on 2007-08-01
I had this same problem but couldn't get the sonar screensavere to work. So I set it to 

blank-only

which returns the screensaver to a blank screen.

---

### Post by laetfut on 2007-08-01
AP's solution worked for me as well.  Is there a way to know what screensavers are 3d or not.  I wasn't too keen on Sonar & wanted to find something else.  I clicked on Solar Winds and my CPU froze again.  I would like to avoid clicking on screensavers that are going to freeze my system..Can anyone recommend a few screensavers that work?

---

### Post by perryrt on 2007-08-01
For what it's worth, I've got the same problem. 

According to [ [COLOR="Blue"]this posting on the Dell Linux support forum[/COLOR]](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=11136), it can also be fixed/enabled by using the prerelease updates (instructions on how-to are in the linked page), and will be fixed "for real" in Gutsy.

Disclaimer - I haven't tried this yet (I will tonight, I'm just at work now), but it seems reasonable. I'll let y'all know if it melts my brand new Inspiron down.

Surprising that Dell would miss something as glaring as 3D support with the video card, though (or perhaps I'm being a bit silly there.)

---

### Post by perryrt on 2007-08-01
As an update - the above solution appears to be working fine.

---

### Post by Nando777 on 2008-01-24
An easier way to change the screensaver without having to edit anything is by turning off the Desktop effects

Go to Preferences --> Appearance --> Visual Effects and choose None

If you do that your system won't crash.

It's been more than a year since this problem was discovered an nVidia hasn't done anything to fix it yet. 

Make sure you delete the screensaver file afterwards by going /usr/share/applications/screensavers/ 

The screensaver name is Braid. something.

---

