---
title: "Linux NetCafe Implementation"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by yokim on 2005-10-08
What's the best thing to do?

Workstations are around 1.5ghz+ with 128 ram built-in video card. Windows and Linux both exist in the network.

I installed ubuntu in each Linux Workstation, and it's kinda' slow in older machines. Another thing, I could'nt remember if I did or the automatic partition assigned some space for swap. So I'm looking for another solution. Before I do something, I want some advice. I could: 

(1) reinstall everything. kubuntu-server then install kde + apps. kde because of the kiosk tool. 

(2) I read something about Ltsp but I think I can only pump a pc with 512ram in 2.3 ghz and there's about 20 workstation.

application: firefox, gaim, open office, x chat will do.

side question:
If I set up a dhcp server, would it "disturb/destroy" the network with static IPs? The dhcp server will not be the gateway.

Would it make a difference if I have a 2GB swap? or 3, 4?


Thank you very much

'hope to hear from you guys soon ^_^

---

### Post by dasunst3r on 2005-10-08
For starters, 2 GB of swap is definitely **overkill**.  Because all these computers really need to do is everyday use and not memory-intensive tasks, 512 MB is the ideal amount.

Also, you may want to use Edubuntu for this because there is a tool called TeachersPet.  Find out more at [http://www.edubuntu.org/TeachersPet](http://www.edubuntu.org/TeachersPet)

May your endeavor be successful! You have our blessings!

---

### Post by yokim on 2005-10-08
[QUOTE=dasunst3r]For starters, 2 GB of swap is definitely **overkill**.  Because all these computers really need to do is everyday use and not memory-intensive tasks, 512 MB is the ideal amount.

Also, you may want to use Edubuntu for this because there is a tool called TeachersPet.  Find out more at [http://www.edubuntu.org/TeachersPet](http://www.edubuntu.org/TeachersPet)

May your endeavor be successful! You have our blessings![/QUOTE]

but adding extra swap to the ideal size will do no harm?

ok I will read more on edubuntu. As far as I've read, I think it could be the one I'm looking for administration issues.

---

### Post by yokim on 2005-10-08
anymore ideas?

---

### Post by jiahanhao on 2005-10-10
i set up a kioskish system at work using gnome, just used some of the lockdown options in gconf-editor. works pretty well, except i haven't locked down the wallpaper, and it seems changing it gives customers no end of entertainment. also, the dhcp server shouldn't have any conflicts with statically assigned ip addresses...

---

