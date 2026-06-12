---
title: "CTRL-Alt-Backspace"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by zero244 on 2007-09-13
When you do this is it risky to the integrity of your hard drive. Or by restarting your desktop is data corruption a serious possibility.
Thanks

---

### Post by Outrunner on 2007-09-13
There is no risk in doing this, unless you forgot to save something you were working on. All it does is restart X, it's no big deal

---

### Post by csimons on 2007-09-13
No, there is no harm in using the CTRL+ALT+BACKSPACE sequence.  This sequence sends an interrupt signal to the X server in Linux and gracefully shuts down the GUI and all GUI programs.  I believe this happens by the X server sending each of those programs interrupts in turn.  The only problem you may encounter from doing this is losing unsaved data.

---

### Post by rsambuca on 2007-09-13
There should be no risk to your HD with this.  All it does is restart your X-server, which is the graphical enviroment.  If you have any programs running within X, you may lose any unsaved data though, since they don't have a chance to close properly.

EDIT:  Too slow today!

---

### Post by eentonig on 2007-09-13
powering down is an other matter. That does indeed gives you a high risk of HD problems.

But ctrl+alt+backspace, allthough not gracefully, should cause any havoc.

However, if you can, it's always better to try to found out which is the actual program that blocks you, and only kill that.

If you enter <alt>+<F1> (or F2....F6, F8..) you are taken out of your current vty (the GUI in this case) and to a CLI environment.
Here you can use commands to figure out who is the bad guy (using top or htop and look who's eating your CPU or RAM) and then kill only that process ("kill <pid>" or "killall <programname>"). This way, you don't have to loose any data.

PS. <alt>+<F7> brings you back to the GUI.

PPS. Sometimes, you can't switch to these other terminals. But (if you have an ssh server running on your pc) what might (usually does) still work, is using another pc to ssh into the problem box. And then search and kill from there.

---

### Post by zero244 on 2007-09-14
Thanks guys for the comments.........very helpful. This forum is priceless for the information you can get.
The truth is most of the advice is better help than what you pay for with other venders.
Thanks again.

---

### Post by dasunst3r on 2007-09-14
If Ctrl+Alt+Backspace doesn't work, you should try Ctrl+Alt+SysRq (SysRq is where the Print Screen button is) before even thinking about holding down the power button for four seconds..  Hold those three keys down while slowly hitting the following sequence: R-E-I-S-U-B

More information: [http://en.wikipedia.org/wiki/Magic_SysRq_key#Emergency_reboot](http://en.wikipedia.org/wiki/Magic_SysRq_key#Emergency_reboot)

---

### Post by FuturePilot on 2007-09-14
I would make sure to log out before restarting X. If you're still logged in, you're basically crashing everything that's running in the desktop. Whereas if you logout, most desktop processes have been stopped.

---

