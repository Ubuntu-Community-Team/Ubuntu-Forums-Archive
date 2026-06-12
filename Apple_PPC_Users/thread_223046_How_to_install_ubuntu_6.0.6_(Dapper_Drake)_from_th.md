---
title: "How to install ubuntu 6.0.6 (Dapper Drake) from the CD"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by Lurcher on 2006-07-25
Generally, something as simple as installing an OS (be it Mac or Windows) generally doesn't bother me all that much, though I cannot say the same for ubuntu at the moment.

I have been attempting to install it on an iMac G3/500 and it appears to load just fine (in fact I am watching the progress bar and getting lots of 'ok's' as the system loads but instead of opening on a desktop or anything my screen is black (though my computer continues to make noises, and in fact that is a bit of music, kinda like the Windows opening chime but more subtle, but the screen is still dark, so I have no idea what's going on. 

Any suggestions as to what I could do would be appreciated.  The computer I am installing ubuntu on is the computer I upgraded from (my main computer is an iMac G5/1.6GHz) so I have no issues with going in there and playing with the command line, as long as I can get things up and running.

My intent was to install ubuntu on the G3, which is my goal.


Thank you.

---

### Post by H.E. Pennypacker on 2006-07-25
I can guaruntee you that the problem does not lie with Ubuntu, because there are millions of people using Ubuntu, including me.  

Exactly at what step are you now?  You've inserted the CD into the computer, and there should be a screen asking you whether you want to run the Live CD or not.  Once you get there, select Live CD.  The Live CD, after a minute or two of loading, will show the Ubuntu desktop as it appears by default.  Once you get to the desktop, there will be an icon for the full installation to the harddrive.  Select that icon, and install Ubuntu.

I believe you are currently stuck on the step after selecting Live CD.  The system, at that point, is loading, and there is a progress bar showing what it is doing.  If that bar does not go away, and the desktop does not load after a minute or two, you probably have a bad burn.  If you're using a CD-RW, try a CD-R, or just try another CD (whichever it is you have).

My best guess is a bad burn, and this turns out to be the answer most of the time.  Just in case, tell us exactly where things go wrong (what message you last saw), and if you are seeing any messages now, let us know.

---

### Post by Lurcher on 2006-07-25
**Exactly at what step are you now? You've inserted the CD into the computer, and there should be a screen asking you whether you want to run the Live CD or not. Once you get there, select Live CD. The Live CD, after a minute or two of loading, will show the Ubuntu desktop as it appears by default. Once you get to the desktop, there will be an icon for the full installation to the harddrive. Select that icon, and install Ubuntu.**

[B]My best guess is a bad burn, and this turns out to be the answer most of the time. Just in case, tell us exactly where things go wrong (what message you last saw), and if you are seeing any messages now, let us 
know.[/B]

I actually never get the the step where I select Live CD.  Ubuntu begins to load and here is the message: Welcome to Ubuntu 6.0.6 with some other information (I began to type it, but it went out pretty quickly).  Then the screen jumps to the progress bar, and a checklist, which my computer seems to do well on (everything is 'ok'.).  Unfortunately I cannot do anything (if the CD is a 'bad burn') other than wait to be sent another because I have difficulty finding CD's larger than 700MB (the disk image for ubuntu is slightly larger than that, if I recall).

**I believe you are currently stuck on the step after selecting Live CD. The system, at that point, is loading, and there is a progress bar showing what it is doing. If that bar does not go away, and the desktop does not load after a minute or two, you probably have a bad burn. If you're using a CD-RW, try a CD-R, or just try another CD (whichever it is you have).**

Once this finished running though, the screen goes black.  As I mentioned prior, there are still sounds, and even what sounds like the chime you get when the desktop opens, but there's nothing there.

---

### Post by linear on 2006-07-25
The magic word is "iMac G3". The Live CD does not set up xorg.conf properly.

After booting is complete,
1. **ctrl-option-F1** (should give you a command prompt - may take a few tries)
2. type: **sudo nano /etc/X11/xorg.conf** (return)
3. make your edits (see below)
4. **ctrl-O** (return) to write edited file
5. **ctrl-X** to exit nano back to command line
6. type: **sudo /etc/init.d/gdm restart** (return) to restart Gnome (note: with the Dapper Live CD, use **sudo killall -HUP gdm** if Gnome won't restart.)

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by Lurcher on 2006-07-25
Coolness.  I'll give it a try and get back:mrgreen:

---

