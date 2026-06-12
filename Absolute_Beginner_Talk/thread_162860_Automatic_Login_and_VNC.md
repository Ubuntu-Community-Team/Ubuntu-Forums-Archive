---
title: "Automatic Login and VNC"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by qw3rty on 2006-04-19
I have Ubuntu installed on a remote PC.  I want to be able to restart the computer and then be able to login remotely with VNC.  I just set it to automatic login.  Is this enough?  I'm afraid to try it because I won't be able to physically get to it for a week or 2.  

Is there something where it will ask for my password the first time it logs in automatically, or will it just work?

I had Windows 98 on the computer before Ubuntu.  On Windows 98, the first time you start up without a keyboard plugged in, at the beginning of the startup you have to click some window saying it's OK to startup without a keyboard.  Do I have to worry about that happening with Ubuntu?

Do I even have to restart the computer?  With Windows 98 I had it automatically restart every 8 hours because it would lock up if it was running for too long without a restart.  It still locked up sometimes even with the automatic restarts, that's why I switched to Ubuntu.

Sorry for the dumb questions, but I guess that is what this forum is for.  I've only been using Ubuntu for about 5 days, and I've never used linux before.

---

### Post by htinn on 2006-04-19
If you set up a user to be "automatically" logged in, then the login screen will not appear at all. The desktop will simply be loaded directly after Ubuntu boots.

If you later decide to log out, then the login screen will appear.

Unless you have problems with the computer crashing all the time, you don't really need to restart (not even Windows, that is since 98SE).

---

### Post by qw3rty on 2006-04-20
I didn't restart or log out.  The computer just froze.  I can still connect with VNC, but now all I see is black.  The screen saver is set to blank screen and I think that is what I'm seeing.  Since VNC is still working, if I had telnet or ssh running I think I could connect and restart the computer even though the gui is frozen.

---

### Post by htinn on 2006-04-20
It may be that the screen saver was set to lock the keyboard. It usually is by default.

---

### Post by qw3rty on 2006-04-20
It's been running for 5 days.  And I didn't have any problems until last night.  I connected with VNC and I could see the desktop, the bottom taskbar and the top menu bar.  But I couldn't see any icons on the desktop, and applications and system and stuff wasn't on the menu bar, only the time was there and it had stopped.  I could move the mouse, but clicking didn't do anything.  Now all I get is a blank screen.

---

### Post by qw3rty on 2006-04-21
Apparently it isn't frozen.  Only the mouse doesn't respond.  I can still use the keyboard.  I think maybe the VNC server is screwed up, because I tried connecting with 2 different VNC clients and the mouse didn't work on either of them.  There was a window open and I could use the arrow keys to select different icons.

Is there a key combination I can use to restart the computer?  Or a key combination to open the terminal or select the top menu bar?

---

### Post by qw3rty on 2006-04-21
Wierd, now the mouse is working.  Something was wrong that made it not respond for 2 days.  But now it works, I didn't do anything different.

---

