---
title: "Trying to stop services I don't need"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-05-28
I wanted to stop services that I don't use or don't need on my system,
so while booting up I saw these two:
 "powernow: This module only works with AMD K7 CPUs"
 "ndiswrapper version 1.8 loaded (preempt=yes,smp=no)"


I then ran "dmesg > boot.messages" and found the above lines.

I next opened synaptics and searched and found "powernow" and "ndiswrapper"
(powernow is from Powersaved which is the power management daemon)
(ndiswrapper--utils is where ndiswrapper is from).
I then UN-installed both of these programs.

But later when booting up again, still checking for services I don't need
I see the same messages again:

 "powernow: This module only works with AMD K7 CPUs"
 "ndiswrapper version 1.8 loaded (preempt=yes,smp=no)"

I then did a whereis ndiswrapper and it came back with
ndiswrapper: /etc/ndiswrapper

I also did a whereis for powersaved too, but it diden't show anything.

So, what am I doing wrong when I did a complete removal and they continue
to run or showup during bootup?

I thank you in advance for taking the time to help me. "Thank you".

---

### Post by Jussi Kukkonen on 2007-05-28
> So, what am I doing wrong when I did a complete removal and they continue
to run or showup during bootup?

They're not actually running (the executables have been uninstalled), but a normal removal does leave configuration files present. This is smart because then you'll still have your config if you decide to reinstall, but it also means the kind of annoyances you saw.

There is a "Remove completely" option in Synaptic, use that to get rid of config files too.

---

### Post by Ozeuss on 2007-05-28
i dunno specifically about these two processes, but have you tried boot-up-manager (bum), or[ sysv-rc- conf]("http://ubuntuforums.org/showthread.php?t=89491")?

---

### Post by housekid on 2007-05-28
I will do a reinstall and then a complete un-install to remove the config
files and if that don't work I will install sysv-rc-conf and go that route.

Thanks again for the fast come-back!!

---

