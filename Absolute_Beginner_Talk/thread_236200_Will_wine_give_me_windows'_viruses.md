---
title: "Will wine give me windows' viruses?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by JReagan1990 on 2006-08-14
I am not quite sure if this is in the right place, but I I install wine, will it give me windows viruses?:confused:

---

### Post by aeiah on 2006-08-14
at a guess, the worst a virus could do is corrupt the program you are running through wine, but the virus would have to be specifically designed for the task, and would have to exploit linux distribution-specific vulnerabilities or rely on the windows software vulnerabilities. most software that people run in wine doesnt behave in such a way that it can download from the internet, and have modifications made to it. perhaps a malicious patch would be able to?

---

### Post by bruce89 on 2006-08-14
Only if you were to run said viruses, and it would only mess up the WINE fake drive, AFAIK.

---

### Post by davebgimp on 2006-08-14
> **JReagan1990 said:**
> I am not quite sure if this is in the right place, but I I install wine, will it give me windows viruses?:confused:

I can't say I've ever heard of that happening. WINE isn't Windows, just a program to help you run EXE files in Linux OS. If somehow that were to happen and I doubt it could, there's not really anything that could happen, I mean, the rest of your system is Ubuntu.

---

### Post by petri on 2006-08-14
Wine itself don't get you any virus :) and windows viruses doesn't "live" in Linux so don't worry about it.

But you can send a virus by mail without knowing it if you have got the virus   by mail and therefore you could install ClamAV with Synaptic to protect your friends. On the otherhand they should have up to date AV program in their Windows, right? :rolleyes:

---

### Post by Bagnaj97 on 2006-08-14
I heard a couple of years ago about someone getting a virus using wine, although it is highly unlikely. Wine is aiming for bug for bug compatibility with windows but as wine isnt running permanently like windows, only when running a program, getting a virus is unlikely. As long as you dont run dodgy programs with wine you'll be fine. Also a virus wont be able to damage your OS unless you are running wine as root.

---

### Post by tht00 on 2006-08-14
> **JReagan1990 said:**
> I am not quite sure if this is in the right place, but I I install wine, will it give me windows viruses?:confused:

Wine doesn't instantly make your computer like running Windows again.  I suppose it's possible to get a 'virus' in your .wine directory through Windows programs you run.  For example, if you would get IE installed and wokring through wine, it is still susceptable to getting infected.  However, keep i mind that viruses and other malware tends to target specific security holes, and will act like it's trying to infect a Windows computer (the .wine directory).  It can't/won't go after anything else in your /home directory, as it doesn't know it exists.

Plus, wine (or Windows) doesn't *give* you viruses.  Computers usually get infected because of the users, not the OS.  Just be smart about it.

---

### Post by JReagan1990 on 2006-08-14
Thanks guys!:D

---

### Post by steve.horsley on 2006-08-14
> **tht00 said:**
> Wine doesn't instantly make your computer like running Windows again.  I suppose it's possible to get a 'virus' in your .wine directory through Windows programs you run.  For example, if you would get IE installed and wokring through wine, it is still susceptable to getting infected.  However, keep i mind that viruses and other malware tends to target specific security holes, and will act like it's trying to infect a Windows computer (the .wine directory).  It can't/won't go after anything else in your /home directory, as it doesn't know it exists.

I disagree, I'm afraid. The default wine setup seems to map / as Z:, so the whole filesystem is visible. So a virus could in theory find and alter any files that the user running wine has write access to. It might even be able to mail out copies of read-only files it finds. Currently, wine is different enough to windows that viruses have a hard time functioning, but it is wine's intention to get better, and that will mean that some viruses and worms will find it a more survivable environment.

---

### Post by empcrono on 2006-09-13
> **steve.horsley said:**
> I disagree, I'm afraid. The default wine setup seems to map / as Z:, so the whole filesystem is visible. So a virus could in theory find and alter any files that the user running wine has write access to. It might even be able to mail out copies of read-only files it finds. Currently, wine is different enough to windows that viruses have a hard time functioning, but it is wine's intention to get better, and that will mean that some viruses and worms will find it a more survivable environment.


i thought about this before and i thought like everyone else before your post.. however that is a pretty good comet

---

### Post by bodhi.zazen on 2006-09-13
At this time it is possible to run windows viruses with wine. They do not run well yet.

[[color=red]How to run a windows virus with wine](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)[/color]

As more users use Linux and wind it is likely to become more a an issue, yet such things are expected to be quashed rapidly.

---

### Post by Eddie Wilson on 2006-09-13
Sorry but no. The virus will not effect your linux os in any way. It doesn't matter if its c: drive or z: drive. It is also easy enough to purge your wine directory. Note that you may have to reinstall your windows app if its affected. Also if you still feel uneasy, run a firewall.

Eddie

---

### Post by Haegin on 2006-09-14
I think I read a post a while ago on these forums where somebody tried running a known infected file in wine and it actually did bring their system down but only because it caused the crash by over stressing the resources or something.
I would say it will depend on the virus you want to install. Some will work, some wont, same as all other programs. Maybe some will work better with cedega or crossover office so you could try them if you really wanted.

---

