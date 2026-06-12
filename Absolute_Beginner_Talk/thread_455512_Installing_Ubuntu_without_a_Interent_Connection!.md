---
title: "Installing Ubuntu without a Interent Connection!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-26
So I've got a friend that is fed up with windows! And they have finally agreed to give Ubuntu a try.

Before they make the switch on there work machine, they want to try it on a older computer that they have. This computer does not have any means to connect to the internet. And even if it did, they only have dial up.

So I thought that maybe I can download the repositories onto a external hard drive. And then add that to their /etc/apt/sources.list some how?

Can this be done? Also how much disk space am I looking at. I would not mind doing this because I have quite a few machines myself and when I update/upgrade or install new software, it uses up a lot of bandwidth. So I thought I could somehow mirror the repositories?

Any ideas?

---

### Post by reacocard on 2007-05-26
> **guysmiley25 said:**
> So I've got a friend that is fed up with windows! And they have finally agreed to give Ubuntu a try.

Before they make the switch on there work machine, they want to try it on a older computer that they have. This computer does not have any means to connect to the internet. And even if it did, they only have dial up.

So I thought that maybe I can download the repositories onto a external hard drive. And then add that to their /etc/apt/sources.list some how?

Can this be done? Also how much disk space am I looking at. I would not mind doing this because I have quite a few machines myself and when I update/upgrade or install new software, it uses up a lot of bandwidth. So I thought I could somehow mirror the repositories?

Any ideas?

The LiveCD should have everything you need to test it on their machine.

I don't know about mirroring the enire repos (probably too much), but there are tools (like aptoncd) that can put packages onto a CD or other media for use as a repository.

EDIT: this thread has a good guide about setting up a local repo: [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

---

### Post by joramdam on 2007-05-26
One thing i am sure of is that you only will get english version, but thats probably no problem ;)

---

### Post by guysmiley25 on 2007-05-28
Yes English is no problem, thank you very much for the information.

---

### Post by oilchangeguy on 2007-05-30
> **guysmiley25 said:**
> So I've got a friend that is fed up with windows! And they have finally agreed to give Ubuntu a try.

Before they make the switch on there work machine, they want to try it on a older computer that they have. This computer does not have any means to connect to the internet. And even if it did, they only have dial up.

So I thought that maybe I can download the repositories onto a external hard drive. And then add that to their /etc/apt/sources.list some how?

Can this be done? Also how much disk space am I looking at. I would not mind doing this because I have quite a few machines myself and when I update/upgrade or install new software, it uses up a lot of bandwidth. So I thought I could somehow mirror the repositories?

Any ideas?

here's a thought, why not just use the live cd on their modern computer. no changes will be made unless you decide to install it. then you won't have to try to add packages to a computer with no internet connection.

---

### Post by guysmiley25 on 2007-05-30
There are applications that they will requirer that are not available with the live CD.

This second computer will still be used as I set it up even after they setup there main machine, as they have no OS for that machine anyway.

But thanks anyways oilchangeguy.

---

