---
title: "Creating a server????"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2008-04-14
Hi there,

I'm a bit of a novice at what I'm about to describe. So I'll try and keep it simple (for my own benefit really).

I have two machines with Ubuntu on (Laptop and desktop). Anyway, I was reading something somewhere about making old computer systems into servers. Now I have an old Pentium 4 machine, which has Ubuntu installed on it too. What I'd like to do is use that old machine for backing up my two other machines on. So what I'm wondering is, is it possible to set my old machine up to just run as a machine for transferring files too and from, and for it to be wireless?

It has a wirelsss card in it. Out of my other two machines, one is wireless, the other is connected via ethernet to a wireless router with built in modem. 

Any tips, would be of a great help. Any links...or whatever. Like I say, I don't really know what I'm talking about with regards servers, so baby steps would be appreciated.

---

### Post by Martje_001 on 2008-04-14
What I have here is the following setup (done with NFS, file sharing for Linux):

```

Desktop ---- Server --- Desktop
                  \
                   ------- Desktop
```
In my /etc/fstab (on all deskops) I have the following line:
```
musicserver:/home/martijn/Userspace/martin/Documenten /home/martin/Documenten nfs defaults,auto 0 0
```
This mounts my 'Documenten' (documents in english) to all desktops, and if I add something to the folder, it automatic gets transferred!

I recommend you to look around for some NFS guides.

---

