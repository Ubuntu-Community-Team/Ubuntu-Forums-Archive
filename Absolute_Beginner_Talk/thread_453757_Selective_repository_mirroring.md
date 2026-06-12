---
title: "Selective repository mirroring"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by sergiodlc on 2007-05-24
Hi:

I work at a large university that is slowly migrating to Ubuntu. We have here a mirror of the official Ubuntu repositories to save internet bandwith. However most of us connect to our intranet from our houses through a 56K modem. This makes virtually impossible to use our repositories at home. I was wondering if there is a way to make a selective copy of the needed packages and transport them in a USB flash memory. For instance, if I'd want to install the [FONT="Courier New"]libgtk2.0-dev[/FONT] package this would be a mess, since it has a lot of dependencies which, in turn, may have subdependencies. Is there a way to automate the process and download only the needed packages? Maybe there is some [FONT="Courier New"]wget[/FONT] hacking to achieve this. 

Burning the entire repositories in DVD is not an option, since many of us don't have DVD drives.

Please, help me.

Thanks in advance,

Sergio.

---

### Post by n8bounds on 2007-05-25
Probably not a perfect solution, but look into what you can do with apt-mirror.  You could, say, make a vm, set it up as a apt mirror, let it sync at work, take it home and configure your sources.list to look at it instead of the public servers. 

I do know that you can go to packages.ubuntu.com and download the deb files from there and do a dpkg -i blah.deb, but of course you have to get every dependency you would ever need for whatever you are doing...it's doable anyway..

---

