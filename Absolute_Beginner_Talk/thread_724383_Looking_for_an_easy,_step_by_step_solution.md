---
title: "Looking for an easy, step by step solution"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by sabresong on 2008-03-14
Hi.

I'm trying to get three [K]ubuntu machines communicating with one another.  Two are HP Slimline s3100n desktop systems, the thrid is an old Toshiba Satellite A55.

All three computers are wired to a Dynex router.

I need the two desktop systems to have access ot each others' home and web directories, and full capabikities (including root and sudo) on the laptop

All the guides I've found either give me just a piece of the solution so I never know what to do first, or assume that I know a lot more than I do.

Can anyone point me to a complete, comprehensive and easy-to-understand guide?

---

### Post by Origin415 on 2008-03-14
It is possible to do this over Samba, but that is generally pretty messy. A better solution is SSH.

```
sudo aptitude install openssh-server
```
On all the computers

Now you can have full command line access by
```
ssh *user*@*ip address*
```

Going to Places -> Connect to Server, you can mount the directory you wish using the SSH option.

As an extra bonus, if you want to share applications, add an -X to the ssh command. Then when you run a command like "firefox" or "nautilus" the application will appear on the computer you ran ssh on, but will act as if it were run on the remote computer, only the graphical part is run on the local computer.


If you need to mount the directories as if they are native hard drives (SSH will only integrate it into gnome, which then integrates it into application that run on gnome), then you need NFS, which is trickier.
There is a guide here:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Installing_NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Installing_NFS_Server)

---

