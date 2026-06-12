---
title: "ntfs hard drive now missing after unsafe shutdown.."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by gottifour on 2008-03-26
Hi all

I had an abrupt shutdown on my computer and now when I try to mount my ntfs harddrives it gives me an error saying I didnt properly unmount my harddrives.. It told me the command to type into the root terminal to fix the problem and I did it. I have two ntfs harddrives and I am also dual booting xp. I can mount one of the other hard dives and also my xp partition but for some reason when I went to mount the other ntfs hard drive it gave me a error. I tried to restart so I could try it again and now it does not show up at all.

Anyone know where I can start.

Thanks for any help...d

---

### Post by northern lights on 2008-03-26
Boot into XP - the login screen suffices - and do a clean exit, with all harddrives connected (in case their external).

Boot into Linux - voila.

---

### Post by gottifour on 2008-03-27
Thanks....I'll try that when I get home..

---

### Post by gottifour on 2008-03-30
It worked great 

Thanks again northern lights!!

---

### Post by northern lights on 2008-03-31
Great. Happy it works and was appreciated.

Personally though I'm not 100% happy with this solution. I do the same when, after booting Windows, my ntfs partitions won't mount. Which they usually wouldn't, cause my Windows is an old install, hardly used, not maintained and takes ages for shutdown.

Question, in the off chance, that someone's still gonna end up reading this: 

Linux won't mount the partitions, but it's aware that theyre present. No commandline solution to clean the cache and the like?

---

