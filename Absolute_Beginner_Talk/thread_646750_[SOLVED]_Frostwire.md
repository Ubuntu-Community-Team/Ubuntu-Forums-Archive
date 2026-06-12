---
title: "[SOLVED] Frostwire"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by teh'p3nsi0n3r on 2007-12-21
i have a copy of limewire which i installed which worked on my Kubuntu Feisty install (no desktop effects like compiz etc) but after installing it on Ubuntu Gutsy i get a white screen when it starts up, after searching the forums i found out that it was due to compiz so i removed limewire and found out about Frostwire so installed frostwire deb from the frostwire website.

This worked fine but only issue now is it will not connect, so far after searching the forums, ive replaced the Gnuttela.net file with some settings i read about in other threads, tried playing with some of the frostwire settings and it still sits at "starting connection...." i dont have any firewall software installed, and ive checked my router settings, thing is limewire works on Kubuntu feisty.

any help apreciated.:)

---

### Post by SOULRiDER on 2007-12-21
You could use limewire and disable desktop effects. I remember there wasa a fix for java apps, i just dont remember what it was. As soon as i find it ill post it.

---

### Post by teh'p3nsi0n3r on 2007-12-21
> **SOULRiDER said:**
> You could use limewire and disable desktop effects. I remember there wasa a fix for java apps, i just dont remember what it was. As soon as i find it ill post it.

Thanks :) i already thought about this and this was the reason i switched to frostwire was the fact it works with compiz-fusion, i'd rather not disable desktop effects if it isnt necessary i use awn dock and emerald window themer so disabling compiz would cause more issues than its worth.
if you can find that fix that would be great, i just cant find any fixes that work so far searching threads.

---

### Post by SOULRiDER on 2007-12-21
Apparently its been fixed. Try updating java
```
sudo aptitude install sun-java6-jre
```
Check this out [http://wiki.archlinux.org/index.php/Xgl_Troubleshooting](http://wiki.archlinux.org/index.php/Xgl_Troubleshooting) although im not sure if its too recent.

---

### Post by teh'p3nsi0n3r on 2007-12-21
ok so i installed that java update and limewire works now but it now has the same issue as frostwire , it will not connect, this is very strange....

i have disabled desktop effect and still the same, will start, but will not connect.

that link you gave me, im assuming thats for the blank screen issue? this is now resolved.

can you think why frostwire and limewire (the deb that connects on (k)ubuntu feisty) will not connect on ubuntu gusty?

im puzzled. :confused:

---

### Post by Crafty Kisses on 2007-12-21
> **SOULRiDER said:**
> You could use limewire and disable desktop effects. I remember there wasa a fix for java apps, i just dont remember what it was. As soon as i find it ill post it.

Yeah there was, hopefully someone can find this. :(

---

### Post by teh'p3nsi0n3r on 2007-12-21
> **Codename said:**
> Yeah there was, hopefully someone can find this. :(

when you say there was a fix for java apps do you mean there was a fix for the connection issue in conjunction with the java applications, or the desktop effects issue? because in my previous post after upgrading to java6, compiz is working with limewire now and frostwire is still ok, but they just wont connect, is this fix for the connection issue?

---

### Post by teh'p3nsi0n3r on 2007-12-21
anyone?

---

### Post by teh'p3nsi0n3r on 2007-12-21
ok i fixed the issue myself, i had a working copy of limewire 4.14 working on my kubuntu feisty install, booted it up and it worked fine "exelent connection" / "super charged connection", booted back up Ubuntu gutsty 7.10, still same issue.
I did install java jre 1.6 after downloading automatix weather or not this had something to do with the fix i applied i do not know.
I tried the gnuttella.net fix which i had a copy of from my kubuntu partion all i did was copy this from the limewire kubuntu feisty partition over the old frostwire ubuntu gunuttella.net file, and guess what, its working pefectly. :)

marked thread as solved.

thanks for everyones help above :)

---

