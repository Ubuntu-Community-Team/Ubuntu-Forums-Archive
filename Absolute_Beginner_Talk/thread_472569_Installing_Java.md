---
title: "Installing Java"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Drewat17 on 2007-06-13
I am trying to install the latest versoin of java. But i am not sure which one to get. I run Ubuntu 6.06. Also I need help trying to install it

---

### Post by Cipher Short on 2007-06-13
[COLOR="DarkSlateBlue"]Ok I am having the same basic question but I am running 7.04 (fiesty fawn).  Also I continue to get an error message when trying to install upgrades , package manager, and the instructions from ubuntuguide.org. It reads
 " E:dpkg was intrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report."
sorry if its confusing that I posted in the persons post but I figured it was kinda basically the same ?? and they may end up with the same problem.[/COLOR]

---

### Post by Cipher Short on 2007-06-13
Oh yea, when I try to run the 'configure' it says I need superuser privligage....Yea, thats me, how do I get it? ( not so much I a "superuser" I'm more like "stupid user" but I still need to get this done for the wife to play her games :)

---

### Post by neo.patrix on 2007-06-13
Sun Java 5 and Java 6 is already in Ubuntu repository,

please refer to this thread for configuring Sun Java 5. 

[http://ubuntuforums.org/showthread.php?t=471488](http://ubuntuforums.org/showthread.php?t=471488)

Same method could be applied for sun Java 6. It is really simple. 

If you are not interested in going thru all those details and just need some jvm , 
then I think GCJ  is also good enough You can install it directlly install using Synaptic Package Manager. It should work out of box, no editing cofiguratin files.

---

### Post by Brendan Hart on 2007-06-13
haha good one, stupid user smart stuff! anyways im having same problem my browser crashes when playing browser games

---

### Post by Outrunner on 2007-06-13
> **Cipher Short said:**
> [COLOR="DarkSlateBlue"]Ok I am having the same basic question but I am running 7.04 (fiesty fawn).  Also I continue to get an error message when trying to install upgrades , package manager, and the instructions from ubuntuguide.org. It reads
 " E:dpkg was intrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report."
sorry if its confusing that I posted in the persons post but I figured it was kinda basically the same ?? and they may end up with the same problem.[/COLOR]

```
sudo dpkg --configure -a
```

Have you guys noticed, there were tons of java related threads today(or am I exaggerating ?), not to mention the dpkg error.

---

### Post by Brendan Hart on 2007-06-13
yeah i have tried alot of threads, made alot of threads , im finally getting used to the installing in multiple ways but nothing is working for me, i even got the same installations as this other person

---

### Post by neo.patrix on 2007-06-13
Does anyone have  the hint???????

Maybe there is something wrong with Sun Java package on repository. Something is broken, everyone has problem installing java.

---

### Post by nvteighen on 2007-06-13
Yes, there's some problem. I get conflicts between sun-java5-bin/sun-java6-bin and ttf-lucida.

I could install java manually from the java website, but couldn't manage to run a local .jar program.

---

