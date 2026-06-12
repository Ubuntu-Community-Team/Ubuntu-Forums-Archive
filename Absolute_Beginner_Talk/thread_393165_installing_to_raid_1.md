---
title: "installing to raid 1"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by superwazn on 2007-03-25
hi guys
i want to install Ubuntu to my old windows machine, but i wasn't sure if anything special needs to be done since the current setup for it is raid1. im not sure if its a software or hardware setup, but i wanted to ask you guys if i should be concerned about ignoring that it is raid1 during installation. sorry if this sounds like a vague question

---

### Post by superwazn on 2007-03-25
anybody? i mean, its alright to just install as if they were 2 regular drives right? nothing will get messed up or anything right? also, if i installed to only one of the disks, would it be able to boot from the other since it was a mirror?

---

### Post by lamalex on 2007-03-25
you will need to tell it to mirror. i forget how ...  it's been a while since ive configured a raid. but as of now your drives are probably not mirroring.

---

### Post by lamalex on 2007-03-25
try looking over this [http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/](http://humandoing.net/past/2007/3/13/software_raid_howto_ubuntu_610/)

---

### Post by superwazn on 2007-03-25
no no, i dont want to setup a mirror for ubuntu, my winXP is already has a RAID1 setup. i checked into it and it seems it isnt software raid either. i want to know if there is anything special about _reformating_ the raid system, like can i "unraid" it so i can keep the second of the 2 mirrored drives for my mom cuz she sure couldnt use linux...

---

### Post by lamalex on 2007-03-25
yeah you can totally do that. just pull the drive out. it might say drive missing but you can ignore that. raid 1 isnt Dependant on the other disk. this is how i close my master server image for clients, i have a machine that has a fully configured set up and a raid 1 with 1 missing driver, ijust put a new drive in, mirror the old one, and pop the newly mirrored drive into my new server. fully configured and ready to go.

---

### Post by superwazn on 2007-03-25
ok thanks! so i can just pull one out, install ubuntu on the one in there, then pop the other back in? and how does this workout for a dual boot? ive never dual booted before so i dont know about that stuff.

---

### Post by lamalex on 2007-03-25
for dual boot you will need to update your grub to recognize the windows partition but yah that should be it. if you're hardware raided you will probably want to disconnect from that too.

---

### Post by superwazn on 2007-03-25
Great! thanks alot. learn something everyday

---

