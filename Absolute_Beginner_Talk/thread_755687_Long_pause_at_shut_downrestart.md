---
title: "Long pause at shut down/restart"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by laffinet on 2008-04-15
Hi,

my computer seems to freeze on shutdown.

I'm running Hardy on a Thinkpad R61i and every time I shut down or restart it exits the GUI, then displays the login prompt (not the login window) and pauses for quite a while (I can not type anything). It eventually displays my computername/tty1 (I think) and resumes shut down or restart.
This does not happen when I simply log out or switch users. Any idea ? Is this a known problem ?

Thanks for the help.

---

### Post by master5o1 on 2008-04-15
Why don't you try opening terminal and typing something like sudo shutdown -P now and see if any error messages get spewed out.

Remember hardy is still in development so they problem may be fixed on your next update.

---

### Post by chrisdugdale on 2008-04-15
If you see the 'no APIC' note at startup this may be a related problem. It is better to leave it, ie don't change to noapic in your booter, cos it just means that it's not a 100% compatible apic, but most of it works anyway and things run faster. I have this situation, ie the no apic message, and the glitch varies, but the solution just seems to be a reboot---sometimes more than once. Sorry I can't remember where I found out about this.

---

### Post by bumanie on 2008-04-15
The same happens to me in hardy. Remember it is still in beta testing. May be I'm wrong, but I assumed the altered boot/shutdown sequence was probably because some work was being done on it and that it has been made like that for a reason and will be fixed/changed prior to final release.

---

### Post by laffinet on 2008-04-15
> **master5o1 said:**
> Why don't you try opening terminal and typing something like sudo shutdown -P now and see if any error messages get spewed out.

Remember hardy is still in development so they problem may be fixed on your next update.

I tried that, no change. 

BTW: When I first installed Hardy I did not have this problem. Only started after a few upgrades/installs.

And I do understand that Hardy is still in development, but there are a few other threads floating around with the same issue in Gutsy. No solution there yet, though.

---

