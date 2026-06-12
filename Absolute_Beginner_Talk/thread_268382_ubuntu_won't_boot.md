---
title: "ubuntu won't boot"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by ObeseOgre on 2006-09-30
I have Ubuntu installed on a seperate harddrive than Windows and when I try to boot Ubuntu i get the message:

mount:Mounting/dev/hdd1 on /root failed: Invalid arguement

and i get a similar message with

/root/dev ... No such file or directory
/sys ... No such file or dirctory
/proc ... No such file or directory

then

/bin/sh: can't access tty; job control turned off

A while ago I reinstalled Windows XP (but it was on a seperate harddrive and I didn't touch the partition Ubuntu was on) but im *fairly* sure that Ubuntu worked after i reinstalled windows xp. I hadn't booted Ubuntu in a while but when I tried to yesterday it didn't work.

---

### Post by BoneKracker on 2006-09-30
It sounds like the filesystem configuration table /etc/fstab did not get set up properly.

What drives to you have (hard disks and cd/dvd) and where are they connected?

Also, boot from the LiveCD, open the terminal, and type:
```
sudo lspci
```
Not sure that will work, but if it does, copy and paste the output into a reply.  Then type: 
```
sudo dmesg
```
Copy and paste it into a reply.

I'll likely be asleep by then, but that should enable somebody to help you.  If it makes you feel any better (or helps someone else pick up where I left off) I suspect that it may be as simple as changing one letter in one line of one file and rebooting:
```
/dev/hdd1    /     ext3      defaults     0 0
```
should probably be
```
/dev/hdb1    /     ext3      defaults     0 0
```
or some similar problem.

---

### Post by ObeseOgre on 2006-10-01
Im not sure about that drives exactly but i'm fairly sure they're "messed up", how would I find out?

When I tried to boot from the Live CD it freezes or gets stuck at a black loading screen.

I doubt this matters but I did get a new monitor since the last time Ubuntu worked.

---

### Post by ObeseOgre on 2006-10-02
> **BoneKracker said:**
> 
I'll likely be asleep by then, but that should enable somebody to help you.  If it makes you feel any better (or helps someone else pick up where I left off) I suspect that it may be as simple as changing one letter in one line of one file and rebooting:
```
/dev/hdd1    /     ext3      defaults     0 0
```
should probably be
```
/dev/hdb1    /     ext3      defaults     0 0
```
or some similar problem.

How would I do that? Thanks.

---

