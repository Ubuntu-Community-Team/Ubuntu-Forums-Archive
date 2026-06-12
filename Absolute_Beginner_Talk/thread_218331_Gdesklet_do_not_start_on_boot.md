---
title: "Gdesklet do not start on boot"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-07-18
I've been playing around with gdesklets and its seems they dont start initially once i begin using my computer, I must run gdesklet shell before they appear, how can I make them appear the instant I log in? As if they were a pannel? 
Thank you

---

### Post by taurus on 2006-07-18
If you want gdesklets to start when you log in, add it to your Sessions...

---

### Post by k420 on 2006-07-18
goto sytem->preferences->sessions than click on the startup programs tab and click the add button and input the command there

---

### Post by Arisna on 2006-07-18
It may work best if you use the command `gdesklets start' for the startup command.  I'm not sure, but otherwise you might end up with the gdesklets shell launching every time and you probably don't want that.

---

### Post by freeflyer57 on 2007-02-13
Thanks! gdesklets start not GDESKLETS SHELL!

---

### Post by falcons7 on 2007-02-13
I've Tried adding it to my startup session using the gdesklets start command. Although it always seems to crash...... any suggestions

---

### Post by Kreat on 2007-06-22
I havn't tried this yet my self, but for the command try this: "/usr/bin/gdesklets"

I found it at another forum, I'm going to try it on my next bootup

---

### Post by Kreat on 2007-06-22
I just tried this command out, and it worked perfectly.  Hope it helps!  I'm still learning my self, so its nice to find some info that could help someone else.

---

### Post by stinger30au on 2007-07-25
I can get gdesklets to start on boot but everytime it starts i get the gdesklets shell.

I have tried starting gdesklets shell and running the desklets i want then exit gdesklet shell and leaving the desklets running and going to system-preferences-sessions and saving my session.

upon startup, no desklets or gdesklet shell :-((

i have also tried adding to the "startup programs" in sessions "gdesklets" as well as "gdesklets start" but everytime i restart i see the gdesklets shell.

the desklets run fine, just want to get rid of the gdesklets shell i see everytime i restart.

Anyone have any ideas??

Thanks

---

### Post by pigbig842001 on 2007-11-05
gdesklets do not start at all

```

nitro@Nitrous-Fumes:~$ gdesklets start
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

```

nitro@Nitrous-Fumes:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

---

