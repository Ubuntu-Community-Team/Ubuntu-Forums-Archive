---
title: "what's the best way to apt-get install *?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-20
Are there some cool ways to basically install everything, even if it makes my install 10gigs? I mean xfce, gnome, kde, all the codecs, all the drivers, etc. It seems like the first thing I have to do when I install is download a bunch of stuff. Packages like ubuntu-restricted-extras are a step in the right direction, are there any more things like that?

---

### Post by Hospadar on 2008-03-20
well
you probably don't really want to do that, aside from the fact that it's not really possible, a lot of packages conflict with each other.  If you want mutiple desktop environments, you can install the different *dm packages and those will pull down the basic environment.  like "sudo apt-get install gdm kdm xdm"  Also, a *full* install would probably take a day(s) and would probably slow your system to a halt if it didn't just corrupt it somehow making it totally unusable.   there's just a *lot* of stuff in the repositories that you will never use.

If your problem is just waiting for dependancies, you will probably find:
a) after a while, most basic dependancies will be installed and you won't have to wait so long

b) you might try going into System->Administration->Software Sources and picking a different download mirror, often you can get better speeds this way.  I think there's even a feature there to automatically pick the fastest mirror.  This can really speed up your downloads.

Another thing too, it's not that everything just has an obnoxiously large set of dependancies, it's just how linux is organized.  Instead of a windows system where you probably have several slightly different copies of a lot of libraries hanging around all over the place, in linux you can have a much smaller set of standard libraries and tools, and it's easy for developers to verify that you have the correct system resources.

Are there any specific features you are having trouble getting to work that some forum trolls like myself could help you with?

---

