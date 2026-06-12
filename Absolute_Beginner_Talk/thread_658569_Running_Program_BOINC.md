---
title: "Running Program/ BOINC"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2008-01-04
I have the BOINC distributed computing platform set up and running.  When I start the program, it runs fine.  I would like to close it, but have it keep running.  When I hit X, it closes, but I don't see it anywhere.  Does this mean it is no longer running?  Do I have to leave it running and in the application bar below (gnome) to make sure I am contributing to the projects?

---

### Post by dcstar on 2008-01-05
> **brandoncolorado said:**
> I have the BOINC distributed computing platform set up and running.  When I start the program, it runs fine.  I would like to close it, but have it keep running.  When I hit X, it closes, but I don't see it anywhere.  Does this mean it is no longer running?  Do I have to leave it running and in the application bar below (gnome) to make sure I am contributing to the projects?

The Boinc Manager only closes, if you have installed the Boinc client from the repositories then it will run automatically on boot-up.

You can confirm this by adding the System Monitor to your top panel, you will see 100% CPU usage consumed by your running Boinc job, and this will still be there after the manager is shut down.

You can stop the running Boinc job in the manager by Activity-Suspend, then you will see your CPU usage drop to almost 0.

---

### Post by brandoncolorado on 2008-01-05
Thanks, very helpful.

---

### Post by Cuppa-Chino on 2008-04-17
maybe a bit far fetched (warning reverse binary logic at work): does this mean that if I only have boinc manager installed and not boinc client, it will require manual start up ? :confused:

here is why I ask: I do not want BOINC to run on its own, I prefer manually telling it to start...

---

### Post by oldos2er on 2008-04-17
Boinc manager is useless without the client, since it's only a GUI to tell you what the client's doing.

---

### Post by Cuppa-Chino on 2008-04-17
so how do I stop BOINC from autostarting ?

---

### Post by oldos2er on 2008-04-17
I'd probably start by looking at [http://boinc.berkeley.edu/trac/wiki/PrefsOverride](http://boinc.berkeley.edu/trac/wiki/PrefsOverride)

---

