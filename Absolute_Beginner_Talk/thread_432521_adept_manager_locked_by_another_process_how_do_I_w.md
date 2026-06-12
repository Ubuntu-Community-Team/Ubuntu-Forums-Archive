---
title: "adept manager locked by another process??? how do I work out what???"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-04
Adept GUI gives me this when I try to open. Just cant work out whats doing it. It was working.


You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

heres my ps -aux, ive checked processes running as root and just cant see where the problem is????

RESOLVED [http://ubuntuforums.org/showthread.php?t=144963&page=2]("http://ubuntuforums.org/showthread.php?t=144963&page=2")

BUT I DONT KNOW HOW IT DID IT ????

---

### Post by igknighted on 2007-05-04
There was possibly another package manager open that didn't show up in ps aux, sometimes if it isn't busy at the moment it can slip through.  Otherwise, there was what is called a "lockfile" that for some reason was not removed when it should have.  This is just a file that blocks you from using two programs at once to change the package database, as that could break your system.  If it is accidentally left in place (a very rare occurrence) then it must be removed, because you cannot use the package managers with it there.

---

### Post by darkworld on 2007-05-04
Thanks for the reply.

think my system is broke and beyound newbie repair.

The above cleared the problem but then when loading packages it told me I had conflicts and couldnt load the package (libxine-main1). Then I was back to original problem, adept locked.

I think I got really desperate to play mpeg4 videos and mp3 the otherday and just started loading up stuff. Think thats where my probs started.

Think im going to reinstall and be a bit more intelligent about what I load next time.

---

### Post by use a name on 2007-05-04
adept is a trouble-maker... Whenever there's a problem, it locks packagemanagement. You could install synaptic instead if you want a GUI.

```

sudo apt-get install synaptic

```
First remove the lock again.

If you have broken packages, try to fix 'm with aptitude (in the terminal). It's not the most intuitive tool, but it is the most powerful.

---

### Post by darkworld on 2007-05-04
> **use a name said:**
> adept is a trouble-maker... Whenever there's a problem, it locks packagemanagement. You could install synaptic instead if you want a GUI.

```

sudo apt-get install synaptic

```
First remove the lock again.

If you have broken packages, try to fix 'm with aptitude (in the terminal). It's not the most intuitive tool, but it is the most powerful.

Thanks for that. i will give it a try first.

---

### Post by TheDoulos on 2007-05-05
My adept database became locked after an add/remove program operation crashed followed by an adept freeze-up.

I used these commands to clear things:
   sudo apt-get -f install
   sudo dpkg --configure -a

See [this thread]("http://ubuntuforums.org/showthread.php?t=348952").

---

