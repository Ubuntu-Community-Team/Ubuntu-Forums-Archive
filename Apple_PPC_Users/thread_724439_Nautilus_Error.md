---
title: "Nautilus Error"
date: 2008-03-14
forum: Apple PPC Users
---

### Post by burroak on 2008-03-14
I start up, log in and get these three messages (even if I live boot).

"There was an error starting the GNOME Settings Daemon.
Something, such as themes, sounds, or background settings might not work correctly.
The Settings Daemon restarted too many times.
The last error message was:
System exception: IDL: omg.org/CORBA/COMM_FAILURE:1.0
GNOME will still try to restart the Settings Daemon next time you log in."

"There was a problem registering the panel with the bonobo-activation server.
The error code is: 3.
The panel will now exit."

"Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server."

I believe that I'm using 6.06, but it's been a while since I've last used this computer (iBook late 2001 model), and I might've installed 7.10.  I have no problem reinstalling, but like I said, I get the same message when I boot from CD.  Any help would be greatly appreciated, thank you.

---

### Post by BladeMelbourne on 2008-03-14
Since it's been a while since you have used your iBook, there are possibly several updates available that may fix your problem.

At a console, run "sudo apt-get update".
(This command will fetch package lists from the internet. If you watch the lines of text scroll by, you will see the name of your Ubuntu version Dapper, Gutsy, or something else.)

Then start synaptic, view by Status, then mark the packages under "Installed (Upgradeable)", then Apply the updates. If you don't have synaptic, you could just run "sudo apt-get upgrade" after running the first apt-get command listed above.

Due to the nature of your problem, I would probably reboot (or at least logout, then login again) to see whether the updates worked.

---

### Post by stream303 on 2008-03-15
Arghh..  the dreaded gnome settings problem...

Aside from some of the other fixes mentioned in the threads, a new recipe turned up saying that creating a new user with fresh gnome settings helps solve this - and mentioning that wiping out all your previous gnome settings and starting new works.

I'm skeptical, but thought I'd throw this out since at this point, it seems like as good a solution as many of the others...

---

### Post by burroak on 2008-05-12
Sorry for the delay.  It took me a while to the the laptop to somewhere I could plug it in (no wireless).  Initially I got impatient and re-installed the whole system, then got to a router and upgraded.  Computer was fine until about 3 days ago and same thing happened.  I tried adding a new user, but it doesn't help.  Maybe it's just too old, or a hardware problem...  I plan on building one soon that is not a PPC.  Anyone want a 2001 iBook?

Oh, and I am running Dapper.

---

### Post by Joeb454 on 2008-05-12
You may want to try advertising it in the Community Market section :) Don't forget to include your location etc. So people know where they are buying it from :)

---

### Post by john_markh on 2008-05-12
> **burroak said:**
> I start up, log in and get these three messages (even if I live boot).

"There was an error starting the GNOME Settings Daemon.
Something, such as themes, sounds, or background settings might not work correctly.
The Settings Daemon restarted too many times.
The last error message was:
System exception: IDL: omg.org/CORBA/COMM_FAILURE:1.0
GNOME will still try to restart the Settings Daemon next time you log in."

"There was a problem registering the panel with the bonobo-activation server.
The error code is: 3.
The panel will now exit."

"Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server."

I believe that I'm using 6.06, but it's been a while since I've last used this computer (iBook late 2001 model), and I might've installed 7.10.  I have no problem reinstalling, but like I said, I get the same message when I boot from CD.  Any help would be greatly appreciated, thank you.

I had the same error this morning using Ubuntu 8.04.
As far as I can see, the reason for mine was corrupted GNOME configuration files. I had to delete the .config, .gnome, .gnome2. etc.

Following that, I've created a small script to BACKUP those files: [http://ubuntuforums.org/showthread.php?t=791431]("http://ubuntuforums.org/showthread.php?t=791431")

Enjoy.

---

