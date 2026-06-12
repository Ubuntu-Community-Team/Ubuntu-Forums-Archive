---
title: "Solution to screen blanking problem"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-02-22
I have FINALLY gotten VNC to work so I can remote into my Gutsy/home computer from my M/S windows computer at work.

But the problem I have is that when I end the remote session by clicking the X at the top of the screen, then the mouse cursor on my home/Gutsy machine is left sitting in the time date display area at the top of the **panel** and thus it will not go into display power saving mode after my 3 minutes inactivity setting because apparently if the mouse/cursor is on the panel and not in a position on the main desktop area, the power saving mode can not function.  As soon as I get home and move the mouse/cursor down from the panel position to the main desktop area the power saving resumes its normal functioning.

Is there any way around this problem ?  Is there something obvious that I am missing here ?  I don't like leaving my screen with the desktop displayed all day long.

Thanks.

---

### Post by freelinuxhelp on 2008-02-22
One thing you can do is, instead of closing the connection on your workstation, close it on the Linux machine - essentially disconnecting yourself.

---

### Post by freelinuxhelp on 2008-02-22
Another option is to right click on the VNC viewer icon on the top left of your VNC viewer window, and choose close, or disconnect.

---

### Post by wpshooter on 2008-02-22
> **freelinuxhelp said:**
> Another option is to right click on the VNC viewer icon on the top left of your VNC viewer window, and choose close, or disconnect.

DUUUUH, of course.  Sometimes it takes me a while, but I keep plugging away until I get there.

Good name !!!

Thanks.

---

### Post by freelinuxhelp on 2008-02-22
So that fixed it?
If so, please mark this thread solved.

If not, let me know, and we'll keep working on it.

---

### Post by wpshooter on 2008-02-22
> **freelinuxhelp said:**
> So that fixed it?
If so, please mark this thread solved.

If not, let me know, and we'll keep working on it.


I'll have to check it when I get home this evening.

Will let you know.

Thanks.

---

### Post by wpshooter on 2008-02-22
> **freelinuxhelp said:**
> So that fixed it?
If so, please mark this thread solved.

If not, let me know, and we'll keep working on it.

Freelinuxhelp:

No, actually that did not work.

What I have found out is that the screen failing to resume going into the power saving mode has (apparently) nothing to do with the mouse/cursor being positioned in the PANEL.

The screen was still on when I got home.  

So I tried the remote again here locally over my LAN and when I closed the session by Xing the terminal window on the machine that was DOING the controlling (which left the mouse/cursor on the controlled machine in the MIDDLE of the screen - not in the panel as before) the machine again failed to blank the screen after my 3 minute inactivity setting.  

BUT once I made a mouse movement on the machine (which of course, I can not do if I am at work or any other remote location) the screen power saving mode resumed functioning again after 3 minutes on inactivity.

Is this a bug in the VNC software or in Ubuntu itself ?

Could this have anything to do with any of the option settings in the VNC viewer ?

Thanks.

---

### Post by freelinuxhelp on 2008-02-22
Hmm. I'm afraid I don't know.
This is a weird problem. I don't even know what log to look at. Don't even know what I would look for actually.

As far as an actual fix for this goes, I'm at a loss, but as far as a workaround goes, there are still a few things to try.

I don't actually use the power settings, would your onitor go off if you logged off? Or rebooted, though that might not be an option.

---

### Post by wpshooter on 2008-02-22
I am thinking that when the remote session is ended that somehow the computer that was being controlled is still somehow being shown that there is still some type of activity that is keeping it from going inactive.  Exactly what that might be, I am not sure.  

Maybe someone else might have an idea ???

Thanks.

---

