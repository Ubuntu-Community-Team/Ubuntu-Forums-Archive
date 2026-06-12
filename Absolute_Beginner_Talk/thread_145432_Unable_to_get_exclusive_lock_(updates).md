---
title: "Unable to get exclusive lock (updates)"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-03-16
Hi everyone,

Could someone please explain what this means and help me to fix it?
Thank you very much.
I go System>Administration>Update Manager and I get this quote.

> 
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first

I've got no package management application running.

---

### Post by atoponce on 2006-03-16
[quote=xyz]Hi everyone,

Could someone please explain what this means and help me to fix it?
Thank you very much.
I go System>Administration>Update Manager and I get this quote.



I've got no package management application running.[/quote] Yeah.  This means that you have a package management software application running.  Whether it be apt-get, synaptic, or update manager.  Are you sure you don't have one of them hiding in another workspace or terminal?

---

### Post by xyz on 2006-03-16
I'm sure I've got nothing running other than Firefox and Firewall!
Could it be a kind of "temporary bug" that will resolve itself?
Thanks.

---

### Post by atoponce on 2006-03-16
Have you checked your running processes?  There may be a zombie process running that needs to be killed.

---

### Post by LordBug on 2006-03-16
I've seen this happen when I accidently double-clicked the update notification icon.  Close out, single-click it, and see what happens.

---

### Post by rjwood on 2006-03-16
if nothing else try logging out then in again---see what happens

---

### Post by fyrefly07 on 2006-03-16
I have this EXACT same problem.  It started about a week ago when I tried to update some of the software and while it was downloading I closed the window that was running.  Now after several logouts and reboots the exclusive lock problem still happens everytime I try to update.  

I checked top in the console but my screen resolution is too small to see more than the top 20 or so processes so I can't locate a PID for apt-get or aptitude to try and kill it....

---

### Post by RacoonBerry on 2006-03-17
I too have the exact same problem when I select the "updates" icon. Mine started a week ago as well after I'd downloaded some updates. I have tried rebooting, checking for other processes running, etc., but nothing seems to work.

If I go into Synaptic Package Manager I get the following error:  "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

So I open up terminal and enter, 'dpkg --configure -a' and get told I must be a SU to run the command.  Then I enter "SU" am prompted for the password, but my admin password doesn't work anymore.

This isn't a new password - it's the same one I've used countless other times to update Breezy.  I don't know what to try next. I'm frustrated because I'm unable to update my system.

---

### Post by RacoonBerry on 2006-03-17
Okay, I've fixed my system...user error (of course!)

I went back to terminal and typed: 

[INDENT] sudo dpkg --configure -a[/INDENT]

The process ran and now Synaptic Package Manager & the Updates feature both work normally. :cool:

---

### Post by gauthamnaggg on 2008-02-24
Well   I  also encountered the same exclusive lock problem.But I tried  pkill apt-get I works for me .:guitar:

---

### Post by oedha on 2008-02-24
> **xyz said:**
> 
Could it be a kind of "temporary bug" that will resolve itself?
Thanks.

mmm......it will resolve if you reboot......

---

