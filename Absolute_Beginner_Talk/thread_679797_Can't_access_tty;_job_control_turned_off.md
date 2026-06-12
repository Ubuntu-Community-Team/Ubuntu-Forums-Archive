---
title: "Can't access tty; job control turned off"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by gonjinetik on 2008-01-27
So I order this Linux installation CD called Freespire. When I put the cd into my computer, the Freespire menu shows up(install Linux, run off of CD). No matter what option I choose, I get taken to a screen with this message:

Busy Box v1.1.3 (Debian 1:1.1.3 - 3ubuntu 3 + 0) Built-in Shell (ash)

bin/sh: can't access tty; job control turned off
(initiramfs)

I'm a noob at Linux, so I don't know how to fix this problem. Does anyone know how to fix this problem?

---

### Post by espressopigeon on 2008-01-27
Well, as a Linux newcomer, you should know that this is one of the most hated error messages in all Ubuntudom (and since Freespire is based on Ubuntu, Freespiredom). It is notorious for being caused by many different issues, so it is difficult to diagnose exactly what's going on. I got it for not having enough RAM install the OS (not that Kubuntu is RAM hungry, I only have 256 MB, Kubuntu requires 320). But it also seems to indicate a problem with your boot loader looking to the wrong partition. Try this thread: [http://ubuntuforums.org/showthread.php?t=292533](http://ubuntuforums.org/showthread.php?t=292533) or this one: [http://ubuntuforums.org/showthread.php?t=279884](http://ubuntuforums.org/showthread.php?t=279884) 

Wait, do have an OS currently installed?

---

### Post by Majorix on 2008-01-27
Can you run in safe mode (or recovery mode or whatever that is called)? Try adding some options at the prompt where it says "boot: " (If there is any, some distros have it, some don't, and I don't have any experience with the distro you speak of) and try booting then.

---

