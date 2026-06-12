---
title: "How do I change the automount path?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by some.hacker on 2006-12-18
When my computer boots up, it automatically mounts my external firewire drive to /media/ieee1394 . How do I change which directory it will automatically mount to? Note: I want a solution that will work if I unplug the hard drive then plug it back in.

[***EDIT***]
Also, how do you change the permissions with which the drive mounts?

---

### Post by dbbolton on 2006-12-18
maybe you will have to edit your grub settings

---

### Post by aysiu on 2006-12-18
Read these two. One of them should help.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by dbbolton on 2006-12-18
i think i misunderstood the question :(


but, i know aysiu and macogw usually have my back ;)

---

### Post by some.hacker on 2006-12-19
Oh, well, I wanted to know how to change the default directory for automounting stuff. I DID end up just changing my fstab so that it just mounts to the correct directory on boot, but i'd still like to know how to change the default automount directory if I can

---

