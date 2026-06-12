---
title: "Upgraded or just added another OS?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-04-26
When I upgraded to 7.04 did it just ADD another OS? 
I apt-get removed a prgram this morning, but when I was browsing floders looking for something else, I noticed it was still tehre. (with stuff in it).

Do I need to boot up in 6.10 and remove it again?

---

### Post by Old Pink on 2007-04-26
No... what?

How did you "upgrade" ? 

Unless you fresh installed, there will be no option of booting back into 6.10. Although the terminals from 6.10 will remain for use in Feisty... is this what is confusing you?

---

### Post by maccawolf on 2007-04-26
YEs, apparently that is what is confusing me. I upgraded through the upgrade notifier on taskbar. but what about the program that I removed? why is it still there?

---

### Post by tonyr1988 on 2007-04-26
I believe that when you just "apt-get remove" something, your config files will remain. If you were looking through your home folder, you may have seen the "residual config" files from the uninstall program.

Open Synaptic, click the "Installed (residual config)" option, right-click what you want to remove, and select "Completely remove" (or similar...I'm away from my computer at the moment).

---

### Post by Sef on 2007-04-26
You need to add --purge when you remove something with apt-get or aptitude to delete the config files.

---

### Post by maccawolf on 2007-04-27
THanks Sef, I will try that in the future.

Right now I have OTHER problems, and they're major. I broke my Ubuntu------

A FRIEND (not anymore,,,lol) suggested I edit /etc/init.d/rc from concurrent=none to concurrent =shell, and now that I've done that, I can't boot at all. (on live CD right now).
how do I change it back when I can't get into it?

---

### Post by Old Pink on 2007-04-28
> **maccawolf said:**
> THanks Sef, I will try that in the future.

Right now I have OTHER problems, and they're major. I broke my Ubuntu------

A FRIEND (not anymore,,,lol) suggested I edit /etc/init.d/rc from concurrent=none to concurrent =shell, and now that I've done that, I can't boot at all. (on live CD right now).
how do I change it back when I can't get into it?

Mount your linux partition after booting from the livecd, and open/edit the file from there.

It may already be mounted. 

:)

---

