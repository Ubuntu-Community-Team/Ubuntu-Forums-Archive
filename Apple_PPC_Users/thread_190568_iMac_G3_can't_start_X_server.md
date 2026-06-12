---
title: "iMac G3 can't start X server"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by slink on 2006-06-06
Hi

I'm trying to run the live Dapper PPC disk on my iMacG3. I choose the default 'live' option and I can see the progress bar reach the end on the graphical installer. Every test is OK until "Starting HP Printing and Imaging System", which I believe is the last one.

From that moment the screen fades to black with no message at all. The boot process goes on as I can hear the bell sound of session startup after one minute.

The 'live-powerpc' option reports no checksums failed.

I've tried the 'live video=ofonly' which reports:

[I]"Failed to start the X server.
It is likely it is not set up correctly.
Would you like to see the X server output
to diagnose the problem?"[/I]

That just leads me to a prompt ( ubuntu@ubuntu:~$ ).

I have tried Breezy Badger and it behaves the same: dark screen at the end.

Surprisingly, 'Hoary Hedgehog' goes perfectly, I can boot and start the session and run Ubuntu with no problem. Maybe it is because it uses a ncurses installer instead of a graphical one ?

I just don't know how to proceed now.

Do I have to check my graphics card? It is a 16Mb ATY Rage128Pro2.

I've read that Dapper Live CD is unable to correctly detect the video on an iMac G3, but I just don't know what to do if using the live-cd.
Can anyone give advice ?

Thanks

---

### Post by linear on 2006-06-06
See this thread: [http://www.ubuntuforums.org/showthread.php?t=190131]("http://www.ubuntuforums.org/showthread.php?t=190131")
 
For the Dapper Live CD, you'll need to use the command
**sudo killall -HUP gdm** to restart Gnome.

---

### Post by Sav on 2006-06-07
Follow the link posted by linear: the system doesn't set properly the video frequencies.

---

### Post by slink on 2006-06-07
Do I need to use the 'live video=ofonly' mode to reach the prompt or is there any other better way?

---

### Post by linear on 2006-06-07
[quote=slink]Do I need to use the 'live video=ofonly' mode to reach the prompt or is there any other better way?[/quote]
You don't need "live video=ofonly" (and I don't think it works on the iMac G3 anyway). When the screen goes black after everything loads, just hit ctrl-option-F1 (may take a couple of tries) to get the shell prompt.

---

