---
title: "Any way out of a lockup (Cube to blame?)"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-20
Happened a few times over the past week.

Not really something I can MAKE HAPPEN.

Just about 2 or 3 times, I've been spinning the cube desktop round, and about half way thru my twist of the cube, it locks.

Nothing responds.

Amarok was playing music the last time it happened, and Amarok carried on playing the current tune, but did not play the next tune.

I just had to hold in the power button to force a shutdown.

Are there any keyboard keys you can hold down that might do anything?

Like CTRL ALT DEL in windoze

---

### Post by p_quarles on 2008-02-20
Ctrl-Alt-Backspace.

And the best part: this restarts the graphical interface, rather than the entire computer.

---

### Post by mivo on 2008-02-20
If the recommended Ctrl+Alt+Backspace doesn't work (it restarts X), you can safely shut down and reboot the system by holding down Ctrl+Alt+PrintScreen and typing REISUB (while still holding down the first three keys).

---

### Post by PiggiePaul on 2008-02-20
> **p_quarles said:**
> Ctrl-Alt-Backspace.

And the best part: this restarts the graphical interface, rather than the entire computer.

Thanks, made a note of that and will try it next time :)

---

### Post by ahsile on 2008-02-20
If you have the experience you can also try to fix things off the command line by trying one of the following:

CTRL-ALT-F1 to CTRL-ALT-F6

Some times you can see what the offending program is by doing this and then using a program like "top" to see where your CPU cycles are going, and then "kill" it.

To get back to the main screen you could then use CTRL-ALT-F7

---

### Post by darkworld on 2008-02-20
I normally do Ctrl+Alt+F2 then login and do sudo su 

then 

/etc/init.d/gdm restart

---

### Post by ahsile on 2008-02-20
> **darkworld said:**
> Hey I came across a very little known, get out of trouble.

Ctrl+Alt+Prt Sc then whilst holding these down type R E I S U B    

This was given as a very last solution to a lock up.

I normally do Ctrl+Alt+F2 then login and do sudo su 

then 

/etc/init.d/gdm restart

The printscreen trick is neat, never heard of that one before this thread... but the gdm restart should be doable with a simple CTRL-ALT-BACKSPACE

---

### Post by glennric on 2008-02-20
> **mivo said:**
> If the recommended Ctrl+Alt+Backspace doesn't work (it restarts X), you can safely shut down and reboot the system by holding down Ctrl+Alt+PrintScreen and typing REISUB (while still holding down the first three keys).

Don't you mean 
Alt-SysRq-r         (Gives raw keyboard access)
Alt-SysRq-e        (sends SIGTERM to all processes but init)
Alt-SysRq-i         (sends SIGKILL to all processes but init)
Alt-SysRq-s        (syncs disks)
Alt-SysRq-u        (remounts filesystems read only)
Alt-SysRq-b        (forces reboot)

I know this works at least.  These are system requests.  It just happens that the SysRq button is also the Print Screen button.  You should also mention that you should wait a few seconds after each letter before going on to the next.  In particular after s and u it is recommended that you wait at least 20 seconds (some sources recommend waiting one minute) to avoid data loss.  Even better is after Alt-SysRq-r, try Alt-SysRq k, which will kill the xserver.  Then you can try Ctrl-Alt-F1.  If that still doesn't work then proceed through the others.

---

### Post by hyperair on 2008-02-20
Another hint with the SysRq magic keys. You don't need to forcibly shut down your PC, or even restart X. All you need to do is kill compiz. 

1. Alt+SysRq+R (raw keyboard access)
2. Ctrl+Alt+F[1-6] (access a terminal)
3. Login.
4. Kill Compiz ```
killall -9 compiz.real
```
5. Ctrl+Alt+F7 (Go back to your GUI)
6. Start a window manager (compiz or metacity). Respective commands to be typed into your run dialog is "compiz" and "metacity". Then you should be able to continue your work, with no lost data.

NB: Alt+SysRq+K is not needed in this set of instructions. If Step 2 fails, then perform the REISUB (BUSIER backwards) one.

---

### Post by swoll1980 on 2008-02-20
good tips thanks. I found once I upgraded my video card I have not had a compiz crash in several months I still have crashes on my laptop though witch is still running an integrated 32bit  intel card

---

