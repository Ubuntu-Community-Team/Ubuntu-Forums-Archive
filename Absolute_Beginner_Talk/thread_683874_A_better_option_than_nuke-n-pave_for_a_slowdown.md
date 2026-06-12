---
title: "A better option than nuke-n-pave for a slowdown?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by aetherspoon on 2008-01-31
I have multiple machines in my home, and the problem machine is a P4 2.26 GHz / 1 GB of RAM / GF4 Ti4200.  The problem is, it runs slow.
No, slower.  Like taking over a minute and a half to accept the password for gksu slow.  A lot of 'little things' are making the machine seem entirely too sluggish and it is probably just cruft from the odd upgrade / changing cycle I put the machine towards.

Originally, this machine was running Feisty Beta, straight gnome-based Ubuntu.  Now it is running XFCE under Gutsy.
Most of the slowdown seems to have come from the Feisty Release -> Gusty Release update.

What's really sad is that the P3 running Feisty still right next to me is actually running better than the P4 now with how slow it is, the P3 is running more, and they're both running xfce (memory leak for xfdesktop and all).



So, what I'm asking is this:  I know I can nuke-n-pave and get rid of all of the cruft. ** Is there a way that doesn't require me nuking the machine?**  I forgot to set up a /home partition, so rebuilding would be burdensome to say the least, and it also puts the machine out of action for a few hours; the machine is being used as both a Synergy server (thus my keyboard and mouse for multiple computers) AND a fileserver.  I'd rather spend longer removing cruft than taking the machine out of action, as at least then it is still usable during that time.

Help?  I know how to do this in Windows, but not so much in Ubuntu, and I'm not even sure where to begin.

---

### Post by philinux on 2008-01-31
That machine should fly.

Have you tried top command in a terminal or system monitor to see whats eating cpu/resources.

---

### Post by emarkd on 2008-01-31
Since philinux is in here on this one, I'll point to the Gutsy's Bugs and Workaround link in his sig.  It's got some good information about Gutsy slowdowns ;)

---

### Post by aetherspoon on 2008-01-31
> **philinux said:**
> That machine should fly.

Have you tried top command in a terminal or system monitor to see whats eating cpu/resources.

Well, depending on if you check the top command or a system monitor, two different results appear.
If you check top, I'm perpetually at around 40 MB of RAM free even though I'm not swapping all that much.
If you check the System Load Monitor, I'm using barely over half a gig of RAM (out of 1 GB). :confused:
Taking up the most memory is Opera and xfdesktop (from the leak), but even on a fresh boot without Opera even running I'm seeing the terrible slowdown.
I'd check it while I'm running gksu for something, but the system is essentially hung until it finishes processing.  Often I'll go to install an update, it'll ask for the password, and the update is finished by the time I can even regain access to my computer.

I checked the bugs and workarounds thread and didn't really catch anything pertaining to this situation, unless I missed something really obvious.
(editted due to a typo)

---

### Post by philinux on 2008-01-31
**trackerd** is the other culprit. System>Prefs> Indexing prefs.

you might want to either turn it off or change the settings.

I've turned mine off.

I've also used system monitor to stop the process and it made a difference.

---

### Post by aetherspoon on 2008-01-31
> **philinux said:**
> **trackerd** is the other culprit. System>Prefs> Indexing prefs.
you might want to either turn it off or change the settings.

Mine is already off.  :(

---

### Post by philinux on 2008-01-31
Ok well if no-one else chimes in with a fix I would not nuke but move home to its own partition. Click the psychocats link it's one of the links on that page. Then you can install gutsy clean without losing all you app settings. I'd backup home and xorg.conf and your sources.list

There's a howto somewhere to detect all installed apps save it to a text file then use this to reinstall all your apps in one go.

---

