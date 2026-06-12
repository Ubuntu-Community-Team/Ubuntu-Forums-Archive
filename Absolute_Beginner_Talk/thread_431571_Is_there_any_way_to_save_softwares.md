---
title: "Is there any way to save softwares??"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ambush_xx on 2007-05-03
Is there any way i can burn softwares that i have downloaded using the package manager on to a cd for a future installation

I have a very slow internet connection and it would be a hassle to download every thing all over again in case something goes wrong.

---

### Post by Sef on 2007-05-03
At [packages.Ubuntu.com]("http://packages.ubuntu.com"), you can download the packages you want.   However, you have to know under what they are listed.

---

### Post by Iarwain ben-adar on 2007-05-03
Hiya,
yeah you can:
just copy the wanted program (and it's dependancies) from /var/cache/apt/archive

Note: i'm not on my box atm, so the exact location could be wrong, but it is somewhere in /var :D


Iarwain

---

### Post by ambush_xx on 2007-05-03
thanks man that was really helpful

But dont you think there should be an option to save these packages to your preferred location

some of these packages take hours to download on a 64 kb connection

---

### Post by lukew on 2007-05-03
> **ambush_xx said:**
> thanks man that was really helpful

But dont you think there should be an option to save these packages to your preferred location

some of these packages take hours to download on a 64 kb connection

I have alittle script which moves the packages onto a seperate parition. If you want to use this simply copy them back into /var/cache/apt/archives.  When you install via apt-get install or synapect it will look in the cache for a valid deb file to install from before atempting to download the software.
 
Luke

---

### Post by ambush_xx on 2007-05-03
> **lukew said:**
> I have alittle script which moves the packages onto a seperate parition. If you want to use this simply copy them back into /var/cache/apt/archives.  When you install via apt-get install or synapect it will look in the cache for a valid deb file to install from before atempting to download the software.
 
Luke


Thanks man thats a relief to hear..

---

### Post by ambush_xx on 2007-05-03
but these files get updated regularly

So when synaptic searches and doesnt not find the newest file wont it try to download it

---

### Post by Iarwain ben-adar on 2007-05-03
Jup, you're right about that.

But as far as i know, it's being discussed for Gutsy to have delta-patches (meaning you won't have to download the full .deb anymore).
Do correct me if i'm wrong :D


Iarwain

---

