---
title: "shutdown sound"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2008-01-15
need to know how to get a shutdown sound to function

so I don't forget to turn off sound system

---

### Post by jryprt on 2008-01-15
> **Rita G. said:**
> need to know how to get a shutdown sound to function

so I don't forget to turn off sound system

Go to  System>Preferences>Sound, Than Sounds tab at the bottom there is Log Out click the bar & go to Select sound file look for shutdown.wav or use something you like.

---

### Post by Rita G. on 2008-01-15
tried that

doesn't work

---

### Post by rfruth on 2008-01-15
does the startup sound work, can U play (test) sounds, ubuntu 'see' your sound card ?

---

### Post by Rita G. on 2008-01-15
startup sound works

---

### Post by rfruth on 2008-01-15
is the shutdown sound grayed out, how about others (question, error, misc) ?

---

### Post by Odd-rationale on 2008-01-15
I had the same problem. For some reason, configuring it through Pref --> Sounds doesn't work. So I did some "hacking" instead.

First, make sure that you have sox installed.

Then open a terminal and do
```
gksudo gedit /etc/gdm/PostSession/Default
```

Add the follow line to that file:
```
play /usr/share/sounds/shutdown.wav > /dev/null 2>&1 &
```
Of course, you can change it to any .wav you want.

Save the file and reboot.

See if that works.

---

### Post by RBEmerson on 2008-01-15
There is a default shutdown sound selected at installation.  If you haven't changed that, you should get a brief sound (a chord from the opening sound, I think) at shutdown.  

However, the problem may not be in selecting a shutdown sound (if one's already selected).  It could be you speakers.  Some speaker systems have an idle mode where the main amp(s) shut off, to save power, but a circuit watches for sound from the computer and wakes the amps back up. I have some old Boston Sound and Altec-Lansing powered speakers that do this.  Typically, they drop back to idle mode after about 5-10 minutes (hard to time this, though, as it's a little like continually asking someone if they're asleep yet... :oops: ). A short sound (like the default shutdown sound) may be over before the speakers are fully powered up again.  To test this, play a CD or some sound *immediately* before doing a shutdown.  That will ensure the speakers are fully powered up as the shutdown sound (if one was selected) plays.

---

