---
title: "[SOLVED] Can't access ACPI events..."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by A Pragmaticist on 2008-02-09
I just upgraded from Feisty to Gutsy, and while it was installing I got an error:

"Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running."

I don't know how to make sure the ACPI subystem is working or the acpid daemon is running, I'd appreciate it if someone could help me out.  For the time being I cannot monitor my battery power.

Also, and I don't know if this is connected to it, but my laptop is running very slowly now.  Not just internet, but every program.  My CPU frequency scaling (governor set for 'ondemand') says that it is working at 100% all the time, and the system monitor says something close to that, but there is hardly any of the blue indicator going up like it did in Feisty.  The temp for GPU core (84 C)  is up a few degrees and the acpi temp(69 C)  is over ten degrees higher from what it was in Feisty.  I have the Watermark screenlet telling me that the cpu load barely goes over 10%, and the RAM is at 16% in the memory meter.

Help?

---

### Post by codeslicer on 2008-02-09
Ok, maybe the services aren't running. Try this:
Go to System->Administration->Services. Enter your password. Now, make sure that "CPU Frequency Manager (powenowd)" and "Power Management (acpi)" are on. If they are, try unchecking then checking them again.

---

### Post by A Pragmaticist on 2008-02-09
Tried that, didnt work.

It wasn't (acpi), it was (acpid), don't know if that matters.  Also, there was another power management, don't recall what it was though.

And somehow the governor is 'userspace' now rather than 'ondemand', though I would have sworn that it was 'ondemand' before, and I did not go in to change it (unless I did it by accident?)

---

### Post by A Pragmaticist on 2008-02-11
bump

---

### Post by A Pragmaticist on 2008-02-11
So now the governor has changed back to "Ondemand", without me changing anything.  How does this happen?  Also, the cpu frequency is always at 100%, which I don't get...it is always like that, even though I am doing nothing.

My comp is running a little bit faster overall, I think it must be due to the governor changing to "Ondemand".  But still it is very slow.  Any suggestions?

---

### Post by A Pragmaticist on 2008-02-11
Okay, I think the "Can't access ACPI events" problem is not actually a problem, I think that was just during the upgrade.  When I turned off power management (acpid), I restarted my comp and it gave me the same warning.  I then turned acpid back on and restarted, and no warning.  So I am going to make this thread "Solved" and post a new thread about the comp running super slow.

---

