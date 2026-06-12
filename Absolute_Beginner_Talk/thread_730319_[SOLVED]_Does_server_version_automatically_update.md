---
title: "[SOLVED] Does server version automatically update?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Deb.Early on 2008-03-20
Hi there! I was a computer professional for 30 years before retiring so I'm not a *complete* beginner at all this, but right now I sure feel like I am!

Question: does Ubuntu (Gutsy, specifically) server version incorporate an "automatic update" feature? If it does, is there any way to completely disable it? I've googled the known universe and cannot seem to find a "yes" or "no" answer to those questions.

The reason I ask is that I have a new machine which I am about to do a file server install on. I haven't done a server install since the days of early RedHat, and after about 2 weeks of research I've come to realize Linux just ain't the same animal anymore. I love my Ubuntu desktop/laptops, but the server is turning out to be another matter -- and now I'm bleary-eyed, sleep-deprived, and completely information-overloaded. Once I get this machine configured and working, I need to put it in the server closet and ignore it until one of us dies!!

I've seen too many reports in these forums of upgrades/updates "breaking" something. The current LTS server is pretty old, Hardy is still too new, I just want to get a Gutsy server going and lock it down so nothing gets changed behind my back. Is this doable?

Thanks in advance!

---

### Post by Nythain on 2008-03-20
no auto update that i've discovered so you should be good... i run a gutsy based home network server myself, great machine... hope you have the same experiences

---

### Post by jimv on 2008-03-20
The only way you're going to get an ubuntu server to auto update is to create a script that runs "apt-get update" and "apt-get upgrade".  That said, it doesn't update on it's own.

---

### Post by Deb.Early on 2008-03-20
Thanks so much to both of you for the really fast replies! Now hopefully I'll be able to sleep once I get Samba wrestled to the ground...  :)

---

