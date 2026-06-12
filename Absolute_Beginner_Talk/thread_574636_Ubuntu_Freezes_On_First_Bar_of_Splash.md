---
title: "Ubuntu Freezes On First Bar of Splash"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Tiggums on 2007-10-13
I am not quite sure even how to describe the entire situation, I used Wubi to get 7.04 Ubuntu on my laptop (toshiba satellite S4074), and it has worked fine for several days, but lately it seems to lock up in firefox and I am forced to reboot, if it locks up I cannot access anything else, so I am forced to reboot, a while after that started happening it would start to load the splash screen for Ubuntu, and stop at the first bar, I figured that it was happening because wubi needed something from windows, so I would log into windows (normally having to run a chkdsk) and then restart the system properly and everything was fine and dandy.  Now I cannot even use that tactic to get into Ubuntu, I am constantly stuck at the first loading bar of the splash screen.  I tried to figure out how to read it one command at a time like windows can, and it sort of worked the same way, except it gives me this huge error message that is something like this:

SysRq : HELP: log level10-8
reBoot crashdump term Full Kill sak ShowMem Nice PowerOff show PC unRaw Sync ShowTasks Unmount Show Blocked Tasks

CheckRoot = bootarg cat /proc/cmdline arMissing Module, devices; cat /proc/modules/1s/dev
ALERT! does not exist Dropping to a shell!

then it proceeds to talk about a busybox which gives me the help option to get some commands, then follows with this:
/bin/shi cant acces tty; job control turned off
(initramfs) show pc
/bin/sh/show pc: not found
init tramfs....

so yeah, I pretty much think my computer is possessed... I don't recall really changing anything, I allowed it to install some updates, but as I said before it really all started with firefox... thanks for any help given...

-Tiggums

---

### Post by shearn89 on 2007-10-13
Wow... umm.... have you tried booting "nosplash" in order to get the full output? If that doesn't work, can you boot to a previous kernel? I'm afraid i don't know anything about Wubi.

On a less serious note, that has to be one of the funniest error messages ever - 
```

SysRq : HELP: log level10-8
reBoot crashdump term Full Kill sak ShowMem Nice PowerOff show PC unRaw Sync ShowTasks Unmount Show Blocked Tasks

CheckRoot = bootarg cat /proc/cmdline arMissing Module, devices; cat /proc/modules/1s/dev
ALERT! does not exist Dropping to a shell!

```
sounds a bit like "Help - all your base are belong to us."  "somebody set up us the bomb!!"


I don't mean to laugh at your misfortune though - don't take this the wrong way.

---

### Post by Tiggums on 2007-10-13
Lol... It doesn't bother me, I had to write it down though which took about 35 minutes... lol oh well, How would I go about doing it with no splash screen?  I've also tried recovery mode (don't ask how I figured that out...) and it went through the entire thing, but it stops and says waiting for root start or something like that I'll have to reset my windows in order to get the actual message, but if it's important I will get it

---

