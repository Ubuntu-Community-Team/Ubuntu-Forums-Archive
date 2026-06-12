---
title: "Creative Live! Cam Voice - can't get it working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by gcrussell1 on 2007-10-21
I've searched through a couple threads mentioning this particular webcam, and one guy seems to have been able to get it to work with Ubuntu (7.04 in his case). Unfortunately, being brand spanking new to Linux in general, most of the thread - [http://ubuntuforums.org/showthread.php?t=508914](http://ubuntuforums.org/showthread.php?t=508914) - is essentially unintelligible to me. I did get as far as downloading the package mentioned in the last post of the thread, but it's specified for 7.04, and when I try to install it I get an error saying> Error: Dependency is not satisfiable: linux-image-genericNow, being as new to Linux as I am, that means approximately nothing to me.

Incidentally, I'm using Gutsy. As for the camera, the power LED isn't on at all, but when I boot back into XP it lights up, so it's not a problem with the camera itself. I'm particularly trying to get running with Skype (or any other client I can use to talk to family back home on their Skype accounts), since that's one of the last things I need to migrate over to become almost completely independent of my XP installation.

Any help would be greatly appreciated, especially if someone has worked through the same problem before.

---

### Post by gcrussell1 on 2007-10-21
bump

---

### Post by gcrussell1 on 2007-10-23
bump again... If anybody has any ideas or any advice on where to start, I'd greatly appreciate it...

---

### Post by starcannon on 2007-11-23
I have the same error here when trying to install Sn9cxxx drivers from linux projects.
Hope someone can tell us the work around.

---

### Post by mitch123 on 2007-11-24
same problem here - please help...

---

### Post by luke1026 on 2008-03-26
Has anyone got any word on this btw... did any of you ever get this fixed????

---

### Post by nathangeffen on 2008-04-01
I have the same problem. I downloaded sn9cxxx from [www.linuxprojects.org](www.linuxprojects.org) to try to get a Canyon CNR-WCAM43 web camera to work under Ubuntu 7.10. Is it worth waiting and hoping that 8.04 will fix the problem?

---

### Post by Lukul on 2008-04-09
Probably no. I tried to install the SN9xxx deb package in Hardy beta and still get the not satisfiable dependency. My webcam is supported by the out-of-the-box drivers, but they seem kind of broken, at least in Skype the picture I get is very green and bad. So I wanted to test these drivers, but no idea how to install them.

---

### Post by DVG on 2008-05-26
When you tried installing that package and it said the dependency wasn't satisfied, it just means that for the package to work it needs "linux-image-generic", which is a part of the basic Linux code. You should be able to just open Synaptic (Main menu> System> Administration> Synaptic Package Manager),search for linux-image-generic, install the latest version of it, and you should be good. I have a Livecam voice and am going to try setting it up soon in Hardy.

---

### Post by ljrossi on 2008-06-06
Same trouble , also couldnt install sn9cxxx

I do have installed linux-image-generic

---

### Post by DVG on 2008-06-06
Ok I see what you're saying. I guess we could look at similar webcam drivers and maybe by chance one of those drivers will work...

---

