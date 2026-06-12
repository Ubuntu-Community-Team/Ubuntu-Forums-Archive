---
title: "random keyboard freeze"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by egoldtech on 2006-09-17
Hi, I just wanto tos this problem:
I have a IBM thinkpad T30,  some time randomly, my keyboard freezes!!
doesnt respond any more,  but everythings still working, mouse, programs,
I can even execute coomand, with copy and paste :) .
Im not sure, it happend only when I have a remote desktop to a windows pc open, because happens randomly and mostly because I have remotes dektops open,all the time .

there is a keyboard service  process? or something like that to restart??


regards
Eze

---

### Post by tribut on 2006-10-30
> **egoldtech said:**
> some time randomly, my keyboard freezes!

I am having the same problems for some time now (Kubuntu Dapper, KDE 3.5.5). The interesting thing is: The keyboard works perfectly in KDM after leaving the KDE session. When frozen however, not even Numlock works.
It does not happen predictably. Just once every few days. Extremely strange. And highly annoying.



felix

---

### Post by Zeratul7 on 2006-11-02
Same here problem here. Keyboard goes randomly completely nuts when using remote desktop to windows machine. I am not sure when this happened the first time, but in Breezy and Dapper it worked fine.

Any ideas anyone?

---

### Post by tarzan on 2006-11-02
i have the same problem :(

---

### Post by kappa01 on 2006-11-28
I've had the same problem in kde 3.5.5 under both Dapper and Edgy on a Thinkpad T43 (1871), but not under 3.5.4 or 3.5.3.  The problem is unique to kde since everything seems to be fine if I use another window manager.  I can fix the problem by deleting ~/.kde and allowing the directory to be rebuilt following a fresh kde start.

This isn't a satisfying work around since I either have to rebuild my kde configuration or restore from a backup.  I haven't figured out what file is getting corrupted.  This leads me to believe the problem won't be fixed by restarting a service.

The next time this happens, I will try to to compare ~/.kde before and after.  Hope someone else will as well and report on the corrupt file.
Paul

---

### Post by jblebrun on 2006-12-27
Next time this happens, check in KControl under Accessibility, and see if "Slow Keys" has been turned on. If so, turn it back off! 

You can run KControl from GNOME or any other window manager.

---

### Post by soujiro14 on 2007-10-17
Bumping this thread as I have the same problem.  I use Ubuntu Feisty 7.04.  7.10 releases tomorrow, I'll post here if the update somehow fixes this.

---

### Post by ejlemay on 2007-11-17
I am having the same problem with Ubuntu 7.10. I had been using 7.04 for several months without problem, upgraded to 7.10 and used it for a few weeks without any issue, so I guess that a software update that was released after the 7.10 upgrade caused this problem.

It's quite bad, making the computer almost impossible to use. For example, I can almost never rename files or folder without copying and pasting via a text editor or some other program. OpenOffice Word Processor is unusable at the moment, as I just can't type in it. When I try to save a file from The GIMP, I also have to copy and paste the file name from a text editor or some other program because it won't let me type using the keyboard, although the rest of the interface is responsive and I can still use the mouse without problems.

USB devices seem affected as well. HP DeskJet printer works fine, but my digital camera is no longer detected when I plug it in. It used to work without any problem, and it stopped working at the same time that these keyboard problems started.

Any idea what might have caused this and how to fix it?

- Eric

---

### Post by visionary on 2008-03-08
The possible solution is here [http://suseforums.net/index.php?showtopic=44988](http://suseforums.net/index.php?showtopic=44988)

Can someone explain that in simple English pls..and the needed ubuntu commands? cause that was ment for Suse i guess..

---

