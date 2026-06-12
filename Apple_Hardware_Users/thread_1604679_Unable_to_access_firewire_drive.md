---
title: "Unable to access firewire drive"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by WanderingOak on 2010-10-24
I just finished installing Lucid Lynx on an iMac7,1. So far, everything looks good, except for the fact that I am unable to access my external firewire drive.  I know that outside of the Mac world, firewire isn't seen very often, but I was under the impression that it was supported. It doesn't show up in the /mnt directory of my new system, or my desktop. Then again, I am new to Ubuntu, and the filesystem looks a bit different from Mac and Debian, the two other *nix filesystems that I am the most familiar with. It shows up fine in Snow Leopard.

I would appreciate any assistance that could be provided.

---

### Post by WanderingOak on 2010-10-24
The problem seems to have fixed itself, after logging in and out of Mac and Ubuntu a dozen times. 

For future reference, where does Ubuntu keep it's mount points? There is no /Volumes directory, /mnt is empty, and my other drives and partitions are not visible at / .

---

### Post by linuxopjemac on 2010-10-25
I think they reside in /media

---

### Post by conundrumx on 2010-10-25
Ubuntu does indeed mount things in /media.  You can use the mount command to check things like this (passed with no options it will list current mounts).

Can Ubuntu consistently see the external drive now, or is it random?

---

### Post by WanderingOak on 2010-10-25
It can see the drive now. However, Ubuntu can not write to it. I just tried to transfer a file over to it, only to be told that it is read-only. The permissions shown under 'ls -l' say otherwise. My Mac partition is the same way. Even /Users/Shared, which Mac sets up to be accessible by anybody can't written to by Ubuntu. Right now, the only way I have to transfer files between my two systems is an SD Card that I 'borrowed' out of my camera.

Could this be a HFS+ issue?

---

### Post by WanderingOak on 2010-10-26
I did a bit of research and figured out that 'read only' issue is probably due to my firewire drive and my Mac partition both being HFS+ with Journalling enabled. I am not sure if I want to disable journalling on my primary Mac partition, or the Firewire drive that is used by Time Machine.
 
So, for sharing files between systems, the best solution would be to go with another external drive. So, from the looks of things, this particular problem is solved.

---

