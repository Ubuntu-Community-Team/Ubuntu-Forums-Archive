---
title: "Synaptic Update Problem"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-10-21
"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first"


The update manager is telling update, yet the above quote is what comes up. I've rebooted and shut-down, let it sit for some hours and then restarted, and there is nothing as far as i can tell running, yet i still get this persisting message come up when i try to update.

Any ideas, please?

thank you,


--
sophtpaw

---

### Post by Kyral on 2005-10-21
Hmmm. I dunno. Try disabling the update notifier, that MIGHT be interfering

---

### Post by sophtpaw on 2005-10-21
[QUOTE=Kyral]Hmmm. I dunno. Try disabling the update notifier, that MIGHT be interfering[/QUOTE]

Yes, but it says that something is running. This is what i need to detect no? This might be another clue. I opened Synaptic Package Manager and it says:
"
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

looks like dpkg is running in the twilight zone somewhere out of sight. Does anyone know how i can stop that. I think that is what is interfering with the Update Manager and Synaptic Package Manager too

thank you,

--
sophtpaw

---

### Post by Kyral on 2005-10-21
dpkg is a part of Synaptic (Well, Apt, but Synaptic is part of Apt and ....)

Might want to call up the System Monitor (System Tools -> System Monitor) and flip the dropdown box to "All Processes" and see if Apt or Dpkg is still running somewhere

---

### Post by sophtpaw on 2005-10-21
[QUOTE=Kyral]dpkg is a part of Synaptic (Well, Apt, but Synaptic is part of Apt and ....)

Might want to call up the System Monitor (System Tools -> System Monitor) and flip the dropdown box to "All Processes" and see if Apt or Dpkg is still running somewhere[/QUOTE]

Tried that now. apt-get; dpkg; don't show on the list! and it says nothing is running. Of course dpkg or apt-get must be running but it doesn't show on screen

??

--
sophtpaw

---

### Post by Kyral on 2005-10-21
What about Synaptic, Update-Notifier, etc?

BTW You know if you are looking at the right list if you suddenly see a LOT of processes that you have no clue (like getty)

---

### Post by sophtpaw on 2005-10-21
[QUOTE=Kyral]What about Synaptic, Update-Notifier, etc?

BTW You know if you are looking at the right list if you suddenly see a LOT of processes that you have no clue (like getty)[/QUOTE]

Update-Notifier is also sleeping - everything on the list is sleeping except gnome System Monitor which is running.

Yes, what about getty. I have 6 of them on my list. What do they mean? You were saying 'if i see a LOT of processes that i have no clue of (like getty)' then....?

should i kill a process or something?

Its getting frustrating not being able to access either synaptic manager or to update. 

Help!


--
sophtpaw

---

### Post by Kyral on 2005-10-21
I used getty as an example as to things you wouldn't have a clue what means ;P

Honestly, I'm running out of ideas. I know the only time I get this error is when I try to run two apt-get or dpkg operations at once (I removed Synaptic 'cause I think apt-get is faster and easier)

---

### Post by David Marrs on 2005-10-21
[QUOTE=sophtpaw]looks like dpkg is running in the twilight zone somewhere out of sight. Does anyone know how i can stop that. I think that is what is interfering with the Update Manager and Synaptic Package Manager too[/QUOTE]
At the terminal, type: ps -A | grep dpkg

If that doesn't bring up anything then maybe something else is the problem.

---

### Post by sophtpaw on 2005-10-21
[QUOTE=David Marrs]At the terminal, type: ps -A | grep dpkg

If that doesn't bring up anything then maybe something else is the problem.[/QUOTE]

shame 'ps -A | grep dpkg' didn't cure the problem.
This is starting to look serious :confused: 

--
sophtpaw

---

### Post by sophtpaw on 2005-10-22
[QUOTE=sophtpaw]shame 'ps -A | grep dpkg' didn't cure the problem.
This is starting to look serious :confused: 

--
sophtpaw[/QUOTE]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


sudo dpkg --configure -a
dpkg: error processing lame (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 lame

Can someone tell me how i can uninstall or reinstall dpkg?

thank you!

--
sophtpaw

---

