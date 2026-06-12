---
title: "No sound anymore"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by talisman on 2005-08-13
It worked fine originally, but now there is no sound at all for anything. I'm not sure where to begin diagnosing the problem. Any help, tips or suggestions would be welcome.

Some basic system info:
I'm running Warty on a 2GHz Celeron Fujitsu-Siemans Amilo laptop with 256MB ram on a 5GB partition. Dual booted with WinXP Home. Also, I have no internet access at home.

---

### Post by phen on 2005-08-13
what have you done before it got broken? what exactly worked originally?

is there a process called "esd" active in your system monitor (applications -> systemmonitor)?

last thing: open a terminal (right click desktop -> terminal), and type:

```
lspci | audio
``` 
or
```
lspci | Audio
``` 
or
```
lspci | Multimedia
``` 

this will list (ls) all pci items of your computer. but you only grab (grep) all entries with audio/Audio or Multimedia in it.  you can also try "lspci" alone

good luck!

kai

---

### Post by talisman on 2005-08-13
Thanks for replying.

Well, all I did was use Synaptic recently to "Smart update". Not sure if that caused the problem.

Originally there was startup music and that drum-type sound when you started apps. These are no longer playing. It seems like everything should be working but it isn't. I tried mucking about to get it working but wasn't quite sure what to do.

I'll do what you asked and see what I get when I get home.

Thanks.

---

