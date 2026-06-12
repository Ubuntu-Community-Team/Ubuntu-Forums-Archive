---
title: "Non compatable graphics card and Partioning drive"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by liquilife on 2006-09-15
Good afternoon,

I really, really want to give Ubuntu a test run. I've been a Windows user since 3.1 but I am honestly ready to give Ubuntu a serious run as an alternative. I do have some confusing items that need to be solved before I can attempt this however.

1. I own a HP computer with an ATI Radeon Xpress 200 graphics card. The first time I installed Ubuntu I could not get a resolution higher then 640x480 or something close to that. I did a lot of searching in the forums for a solution but found nothing concrete or anything that made sense to me anyways. I found where lots of people were having these issues but no difinitive solution. Can anyone explain to me how I could achieve 1280x1024 resolution with Ubuntu and my graphics card in a way that makes sense to a new *nix user?

2. How could I go about safely and correctly partioning my hard drive for a second OS (Ubuntu)? Is there the the holy tutorial on achieving this that can explain this to someone who has never partioned a hard drive before? My first experience was a mess on doing this.

I really want to give Ubuntu a fair chance and could probably convince others to do the same if I get it running like a champ as a 2nd OS on my computer that doesn't require some uber *nix geekyness. Can anyone help me here?

I hope I am not sounding like a a smart-*** or anything. I'm a guru at using Windows but it just doesn't seem to apply directly to Ubuntu. Thanks!

---

### Post by ieee488 on 2006-09-15
1.) For me, I re-booted and selected the Recovery Mode option. You end up at a command prompt similar to DOS, type in 
[FONT="Courier New"]dpkg-reconfigure xserver-xorg[/FONT]

2.) I had a spare hard drive, added it to my PC, and installed Ubuntu to it. Ubuntu was smart enough to choose the 2nd HD for the install. Installed Ubuntu and then SUSE 10.1 to it.

Good luck!

---

