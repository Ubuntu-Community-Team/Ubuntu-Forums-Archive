---
title: "Dependency errors with Synaptic"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by bearswatchin on 2006-09-24
I am relatively new to Linux and very new to Ubuntu, dapper release.
Recently installed a TV tuner card which works fine in Win2k. The card is a Hauppauge WinTV GO-Plus.

When I try to install any of the programs which should use the card, I get dependency errors during the install. TVTime won't do anything but display the last channel viewed in Win. MythTV has a problem with My-SQL. FreeVo has a database problem and won't connect to the database (My-SQL, again?)

Can anyone point me to a source to learn how to solve dependency problems?

I am running an older Dell product, 500 mhz, 384meg ram and have installed Ubuntu on a 30gig hd with the entire drive dedicated.

Any help will be much appreciated.

BW

---

### Post by lamego on 2006-09-24
Have you edited your sources.list and added extra repositories ?
Usually you get dependencies problems when you are missing the extra repositores or when you added some non official repository which may break your system.

To add extra repos:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by bearswatchin on 2006-09-24
Yes, I added the repositories using cut and paste from the Internet. Some repositories have been non-official, I think. I have been using Debian sources for these trials. Do I understand correctly that I can do that with relatively few, if any, problems?

> **lamego said:**
> Have you edited your sources.list and added extra repositories ?
Usually you get dependencies problems when you are missing the extra repositores or when you added some non official repository which may break your system.

To add extra repos:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by bearswatchin on 2006-09-25
I appreciate the one response I got to my query. I figured it out for myself and will take appropriate action to correct my problem.

Moderator: you can remove this thread, if you so desire.

thanks,
bw

---

### Post by lamego on 2006-09-25
> I have been using Debian sources for these trials. Do I understand correctly that I can do that with relatively few, if any, problems?
Using debian repositores on ubuntu can cause you many problems, it can even get your system into an unrecoverable status.

---

