---
title: "[SOLVED] .deb installer error neeed help"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by IISpII on 2007-11-22
I  reinstalled my system so that i could get a  fresh start but when i went to go and install envy for my nvidia card it came up with this. i dont know what happened and it dident do this before.

[http://www.stashbox.org/52999/Screenshot.png](http://www.stashbox.org/52999/Screenshot.png)

i am using a sony vgn-sz491n/x if you need specs.

plz help :(

---

### Post by bumanie on 2007-11-22
Is it gutsy gibbon you've installed? If so check whether there is an active internet connection.

---

### Post by IISpII on 2007-11-22
how would i be on the fourms if i dident have a active conection

---

### Post by bumanie on 2007-11-22
Some people have 2 computers. Some people have an dual boot with xp where the internet works under windows and not under ubuntu. Some people post problems from their work place looking for an answer to try when they get home.

---

### Post by IISpII on 2007-11-22
oh... well i dont, and to backtrack i do have a active interweb connection

---

### Post by Partyboi2 on 2007-11-22
Have you got  universe and multiverse  repositories  enabled?[COLOR=red][/COLOR]

---

### Post by IISpII on 2007-11-22
yep

---

### Post by Anicka on 2007-11-22
Have you tried to install the missing dependency? ```
sudo aptitude install xserver-xorg-dev
```Thereafter envy should install fine.

---

### Post by erginemr on 2007-11-22
Hello,

Such error messages occur when there is a compatibility issue between a package you have in your system and the version of the package the Debian package depends on. Possibly, you already have the xserver-xorg-dev package installed, but Envy needs a later or former version to work. 

You may try uninstalling xserver-xorg-dev with:
sudo aptitude uninstall xserver-xorg-dev 

and let the Envy Debian package to re-install the correct version.

Good Luck.

---

### Post by erginemr on 2007-11-22
> **Anicka said:**
> Have you tried to install the missing dependency? ```
sudo aptitude install xserver-xorg-dev
```Thereafter envy should install fine.

I believe this is not the case. GDebi (the Debian package manager) should have resolved and installed dependencies automatically. It seems this is rather a compatibility issue.

---

### Post by IISpII on 2007-11-22
ummm........ i feal like an idiot right now, but i just relized i was using the relese candiate and not the stable version. im gunna go and get the right edition, sorry

---

### Post by erginemr on 2007-11-22
> **IISpII said:**
> ummm........ i feal like an idiot right now, but i just relized i was using the relese candiate and not the stable version. im gunna go and get the right edition, sorry

no problem. take care.

(could you please mark your thread as solved from the "thread tools" menu at the top of the page?)

---

