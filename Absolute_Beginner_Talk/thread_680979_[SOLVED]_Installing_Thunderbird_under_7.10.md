---
title: "[SOLVED] Installing Thunderbird under 7.10"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by ElvisGump on 2008-01-28
I'm brand spanking new to Ubuntu (not even 24hrs in) and I'm clueless and stuck trying to install Thunderbird. I've opened the Add/Remove app and when I try to install Thunderbird from there I get the error message:

 "The list of applications is not available
Click on 'Reload' to load it. To reload the list you need a working internet connection."

Since I obviously have an active internet connection I'm stumped. I downloaded the latest  installer from the Mozilla site but don't know what to do with it and searching through posts all morning every solution assumes knowledege I seem to be missing. 

I assume I may need root access because using Synaptic Package Manager or trying to move the .gz around I'm denied permission.

Help!

---

### Post by philinux on 2008-01-28
Have a look in System>Admin>Software Sources

Make sure the top 4 are ticked. And under the third party tick the first and third ones.

If you've not got medibuntu yet click the link below and follow the procedure to get this source.

These are the servers where the software is downloaded from otherwise known as repo's

---

### Post by jan quark on 2008-01-28
perhaps you have to enable the source to be able to install via add/remove
go to the sources in the menu  and check all available sources if they are unchecked

and here a guide for installing stuff in ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ElvisGump on 2008-01-28
Thanks folks, I'll try those, though I have to dash out and can't try them right away damnit.

This whole experience takes me back 15 years when before I was a Mac and Windows user to the time when all I knew about computers was HAL9000 from "2001" a friend sat me down in front of his SGI Indy and I puzzled over command lines and IRIX. 

I feel like a babe in the woods again...:)

---

### Post by ElvisGump on 2008-01-28
> Have a look in System>Admin>Software Sources

Make sure the top 4 are ticked. And under the third party tick the first and third ones.


I already did that at some point following another tutorial, just double checked it to be sure. Still no permission access to installing.

> If you've not got medibuntu yet click the link below and follow the procedure to get this source.


When I do the steps to get medibuntu in the terminal window I get this error:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm logged into my account, doesn't that make me the administrator? I didn't set up any other account when prompted by the ubuntu install process.

I did some of the stuff in the monkeyblog links but I don't seem to be able to get access to anything in the root, which I assume is what the file browser calls "File System".

All I can figure is I'm not understanding how to get ultimate administrator level access which most of these tutorials seem to assume all but us absolute cold start beginners know.

I think the joke goes something like, "Someday we'll look back on this moment and plow into a parked car."...

---

### Post by ElvisGump on 2008-01-29
I guess I must have had some sort of glitch the other day trying to use Synaptic Package Manager because today after a restart I was able to get Thunderbird and a couple of other things just fine. 

During that same boot cycle I kept having problems with the wireless on my laptop occasionally re-requesting my WPA password, so I guess I must have had some general errors with the boot process or something. 

One thing that happened after restart was that the update manager thing kicked in and updated me to the latest Firefox which is what I was trying to also install in the first place along with Thunderbird, so I assume the updates might have added some library or widget I needed not in the CD install?

Anyhow, Thunderbird is running, profiles successfully imported from my Windows profile folder and I'm a very happy camper.

 I can't believe how snappy and responsive ubuntu is after how suffering the pokey performance of my laptop under XP. I may never go back!

---

