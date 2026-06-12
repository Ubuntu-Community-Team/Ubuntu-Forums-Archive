---
title: "Newbie - Xfree86 problem"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by twigmeister on 2006-07-12
Hi,

I'm new to the whole linux revolution and having tried SUSE to no avail I'm playing with XUbuntu.

I've got a VmWare based XUBuntu system running well. Easy to install :) but I'm trying to install VM-Ware Tools.

it's extracted okay and begun to install but about half-way through I get the following message:

[i]before runing VMWare Tools for the first time you need to configure.... invoke the command for you now? [YES]

This program is to be exectued outside of the XFree86 session. Please shutdown all instances of XFree86.

Execution aborted.[/i]

Ok I've seen this before in SuSE and I dropped to a console session and off I went. I cannot find this in Ubuntu.

Help please :)

---

### Post by steve.horsley on 2006-07-12
The command to shut down X (Ubuntu uses x.org, not XFree86) is:
sudo /etc/init.d/gdm stop
and to restart it afterwards is of course
sudo /etc/init.d/gdm start

---

