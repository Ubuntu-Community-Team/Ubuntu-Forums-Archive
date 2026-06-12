---
title: "how do ya upgrade to a newer version"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2008-01-30
if i can manage to install ubuntu 7.10 (no, i cant say those cute little names). anyway if i set it up with a swap and a root, how do i go about upgrading when the next 6 month update occurs??? i really wanna do this but there ARE a lot of obsticles to it :-( btw, what does sudo really mean???

---

### Post by JoshuaRL on 2008-01-30
Try this:

[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

It's a sticky at the top of this forum.

Sudo stands for "superuser-do".  It allows you to be in a non-admin account while occasionally being able to have admin priviledges.  It keeps your system much more stable than just letting you run in an admin (linux calls this root) account.

---

### Post by jaytek13 on 2008-01-30
There are actually no obstacles whatsoever. Whether you use synaptic or adept, both of these offer a "version upgrade" that simplifies the process. Selecting this will install, remove, replace, or upgrade any packages that were changed from ubuntu version x to ubuntu version y and the result is a complete upgrade to the new version... of course there's the caveat that this can sometimes cause some unwanted things to happen, but we can cross our fingers.

As far as what does "sudo" mean... uhm... Well, the original iteration was actually su. su was a command to change to the root user, or the "SuperUser." What does the do mean? I dunno.

---

### Post by Jbirdie1 on 2008-01-30
tks for the timely reply...ok, lets say that i have ver 7.04 installed...now i understand from the post that i  get the new file and use an installer...so then i need to d/l the .iso for the new version ( i will do this on windows and make the cd using windows) now exactly how do i propogate all this stuff on the cd, to the production disk??? i cant fathom this operation and yes, i have been in the computer biz for almost 40 years and this process doesnt make sense...all i will have is a cd ,made from an .iso file...HOW DO I ACTUALLY RUN  SOMETHING thats on it??? i am severely confused about this issue help

---

### Post by RomeReactor on 2008-01-30
Hi. It's not really necessary to download and *use* the new version's ISO to upgrade; the system's Update Manager will notify you when the new version is available, so you can upgrade directly. However, the points on the upgrade guide are valid: **Always** backup before an upgrade; make sure to disable third party repositories you have added manually; and, as a safety measure, download and burn the new version image, and test it just to make sure it works and to have an insurance that if the upgrade somehow fails, you can still do a clean install of it.

---

### Post by jrz on 2008-01-30
Although retired for over 10 years from AT&T using unix about 30 years we always referred to su as "Switch User", and you could 'su root" or 'su bob' or any other user if you also knew the password for that user.

---

### Post by tdrusk on 2008-01-30
> **jrz said:**
> Although retired for over 10 years from AT&T using unix about 30 years we always referred to su as "Switch User", and you could 'su root" or 'su bob' or any other user if you also knew the password for that user.
Nobody's really wrong according to wiki.
[http://en.wikipedia.org/wiki/Su_%28Unix%29](http://en.wikipedia.org/wiki/Su_%28Unix%29)

---

### Post by sistoviejo on 2008-01-30
> **Jbirdie1 said:**
> tks for the timely reply...ok, lets say that i have ver 7.04 installed...now i understand from the post that i  get the new file and use an installer...so then i need to d/l the .iso for the new version ( i will do this on windows and make the cd using windows) now exactly how do i propogate all this stuff on the cd, to the production disk??? i cant fathom this operation and yes, i have been in the computer biz for almost 40 years and this process doesnt make sense...all i will have is a cd ,made from an .iso file...HOW DO I ACTUALLY RUN  SOMETHING thats on it??? i am severely confused about this issue help

Easy way:
An orange lit icon usually appears on the notification area notifying when a full distribution update is available.
Just click on it and confirm to download and upgrade to the new version.
That should do it. 
It would also be smart to follow RomeReactor's advice.

---

