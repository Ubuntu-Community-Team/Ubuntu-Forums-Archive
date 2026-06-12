---
title: "Partition editor on gutsy live cd doesn't see HD"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-10-27
I have successfully loaded the gutsy live CD onto a machine that gives me a periodical boot error that I haven't been able to fix (see thread [http://ubuntuforums.org/showthread.php?t=554013](http://ubuntuforums.org/showthread.php?t=554013)
despite banging my head on it for days; I finally decided to wait for gutsy.
Now, usng teh live CD for gutsy,  the gnome partition editor does not detect any hard disks, so I can't tell it where to install., and where not to install.  This is critical since it's a a dual boot (winXP) machine containing the troublesome Feisty installation that has never worked properly. I had no problems at all with the four other similar machines here that went well straight out of the box, with Feisty.

Have I forgotten something critical? Or might this be related somehow to the problem I have with the fesity installation, which seemed to go well but which will only boot after closing a windows session?

---

### Post by p_quarles on 2007-10-27
That's very odd. I would wonder if your disk is corrupted, at least partially.

I would give the GParted live CD a shot. It's a small download, and it's a dedicated partition editor, so you might get better results.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If it spits you into a terminal on bootup, this is because it doesn't detect all video cards. Just type "Forcevideo," then select the VESA driver and the default resolution (like it says).

Anyway, it might be as simple as needing to format the current Feisty partition. If that doesn't do it, I'd be worried about the health of the drive.

---

### Post by ginestre on 2007-10-28
> **p_quarles said:**
> That's very odd. I would wonder if your disk is corrupted, at least partially. 
The downloaded gutsy md5ed properly, so that ought to be OK. Unless you mean the HD? But it seems to work perfectly well in all other respects, though, if this is the root of the problem.

> 
I would give the GParted live CD a shot.


Thanks for this;  I'm downloading it now and wil give it a buzz.

---

### Post by ginestre on 2007-10-28
Wel, the GParted live cd didn't help at all; or rather, I couldn't get it to help. It loads apparently happily, getting finally to a console; but I can't do anything because every keypress counts double, so if I press (for example)  F I get FF. The delete 
key worksd double too, so I can only rub out both of the Fs.

---

### Post by p_quarles on 2007-10-28
The doubling of the letters might be a video problem rather than a keyboard problem. Did you try just entering the command (Forcevideo) without paying attention to what it says on screen? Worth a try.

By the way, when I said that I'm worried your disk might be corrupted, I meant the HDD, not the CD.

---

### Post by ginestre on 2007-10-28
> **p_quarles said:**
> The doubling of the letters might be a video problem rather than a keyboard problem. Did you try just entering the command (Forcevideo) without paying attention to what it says on screen? Worth a try.

 CD.

Sadly it's not just a display issue- the kybd registers 2 of everything

---

### Post by p_quarles on 2007-10-28
That's pretty strange. Are you using a USB keyboard by any chance? If you have a PS/2 keyboard around, or can borrow one, you might have better luck with that.

---

