---
title: "have to push power button on shut down..."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by JReagan1990 on 2006-10-28
I have a hp pavillion 6642D desktop (oldshool!) and it is running edgy.  On shutdown, the progress bar completes its trip, and my computer does not turn off, it just hangs.  Then, if I hit the power button, (on front of machine!), my computer turns off. 

Any suggestions on how to fix this?

---

### Post by dbott67 on 2006-10-28
Just to clarify, the OS has shutdown, but the computer is still powered on? 

What happens if you type **sudo shutdown -h now**?

EDIT: there is another switch -P that can be used with shutdown that is supposed to force a POWERFF.  There is also a command **sudo poweroff** that you can try.

---

### Post by daxLeet on 2006-10-28
This happens to me when running the live disc, for anyone who could help.

---

### Post by JReagan1990 on 2006-10-28
*sigh*  none of the above commands change the outcome.  And, yes, the os has shut down, but the computer is still on.](*,)   

Thanks for all the suggestions, though!;)

---

### Post by kvonb on 2006-10-28
Look in your computers BIOS under power management, you either need to turn it on, or off, try both!

From memory (which is not too good these days!), you will need to hit a key when the computer first turns on, usually it is the [DEL] key, but on HP/Compaq it is some combination of the following:

[CTRL] [F12]
[CTRL] [F10]
[F12]
[F10]
[CTRL] [ALT] [ESC]

If you have a manual that came with the computer, look for something about changing BIOS or CMOS settings.

Also when the computer first turns on, watch the screen for instructions on how to enter 'SETUP' or 'CMOS' or 'BIOS' etc.

I'm vague because there are so many different ways of getting into BIOS, and different names for it too!

But once in there, play around with the power management settings, that should help.

Regards,  Kev :)

---

### Post by DaveBorealis on 2006-10-28
Here's a thread that offers a detailed possible solution:
[http://ubuntuforums.org/showthread.php?t=276642]("http://ubuntuforums.org/showthread.php?t=276642")

It involves adding "acpi=force" to /boot/grub/menu.lst.

Best regards,
Dave

---

### Post by kylevan on 2006-11-04
I was cruising my directory structure today and saw in /etc/default a textfile named halt.

giving a good ol' fashioned sudo vim /etc/default/halt (or gedit, or whatever you like) reveals the following

```

# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff

```

worth checking to see if it's set to halt.

---

