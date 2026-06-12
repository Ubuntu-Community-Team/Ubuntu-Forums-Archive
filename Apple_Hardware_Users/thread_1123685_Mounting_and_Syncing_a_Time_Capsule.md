---
title: "Mounting and Syncing a Time Capsule"
date: 2009-04-12
forum: Apple Hardware Users
---

### Post by kuniyori on 2009-04-12
Hi everybody. I have bought two 1GB Time Capsules and Im having quite a few problems... to put it mildly...

I want to use one of them as NAS for a mini cluster I have and then I would like the other one to act in a similer way to RAID (for this part Ive been looking at rsync but Ive never had to use anything other then basic cron jobs).

Im having problems even connecting to the capsules so any step by step info would be of great help.

(If I can get this working Ill produce some how to guides after.:popcorn:)

Thanks!

---

### Post by cyberdork33 on 2009-04-13
Well, what protocol do they use to share? afp? samba? nfs? Once you figure that out, it shouldn't be too difficult. 

I don't think you will get to the point of using one of the TimeCapsules for RAID (raid is not a backup solution, it is an availability solution), but if you are just trying to sync a filesystem / backup, then rsync is a good choice. There are also some new apps that work similar to timemachine:
[http://flyback-project.org/](http://flyback-project.org/)

---

### Post by xdracco on 2012-09-24
I could be wrong here but the only method of sharing your Time Capsule is via AFP. That's what Apple uses. Unless you hack the Time Capsule, I'm afraid you're stuck using AFP. Why not return the Time Capsule and invest in a couple of 2TB drives and set up Ubuntu with Netatalk? With Netatalk, you can set up a network volume to be your time machine backup drive.

I'm pretty sure NAS and raid, concerning the Time Capsule, is not going to happen without some hacking of the Time Capsule OS (whatever that may be).

Also, I've heard nothing but "i can't connect to my Time Capsule from my Mac" complaints from a lot of people. Personally, Time Capsule is totally not worth it. You'll have more flexibility with hard drives.

Note, I don't suggest using USB drives for Time Machine volumes.

---

