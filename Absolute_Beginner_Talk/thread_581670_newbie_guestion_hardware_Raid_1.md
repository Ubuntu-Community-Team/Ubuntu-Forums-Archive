---
title: "newbie guestion: hardware Raid 1"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by cybergalvez on 2007-10-19
Hi all, 

I've got a question about install ubuntu on a new computer I'm building.  I'm going to be using a gigabyte MB which has the nvidia chip set and supports a hardware based raid 1.  When I did this from windows (XP) I had to install a raid driver so that windows would see the raid and install properly.  This is not going to be a dual boot so I will formating the HD (or getting new ones, depends on cost) so I really don't care about the data currently on the drives.  So will I be able to install Ubuntu on raid, where can I find info on how to do this?  Do I have to use the fakeraid setup I've read a little about? or will I be able to use the hardware based one (I would prefer to use the hardware based one if possible).

thanks for any and all help
Jose

---

### Post by ice60 on 2007-10-19
there are some articles on the ubuntu wiki, if you are sure you are using hardware RAID i would have thought you shouldn't follow a fakeraid guide because fakeraid means sofware raid, somewhere in the BIOS i think.

if it helps you can run this to get more info about the hardware -
sudo lshw

i'm no expert i was just looking at unanswered posts and saw yours! lol

---

### Post by cybergalvez on 2007-10-19
> **ice60 said:**
> there are some articles on the ubuntu wiki, if you are sure you are using hardware RAID i would have thought you shouldn't follow a fakeraid guide because fakeraid means sofware raid, somewhere in the BIOS i think.

if it helps you can run this to get more info about the hardware -
sudo lshw

i'm no expert i was just looking at unanswered posts and saw yours! lol

Interesting, I just spent some time reading the wiki on raids (all very confusing) and from the sound of it I bet my new gigabyte MB will have a fakeraid installed and not a real hardware based raid.  if thats the case then It sounds like I'm really better off using the software raid described in the wiki.  Since I really don't have much experience setting up all the partitions and stuff like that does anyone know how easy it is to do from the ubuntu installer? 
Jose

---

### Post by cybergalvez on 2007-10-19
One more question,
If my MB does have a real hardware raid, then if its enabled and I've created a raid set, then when I'm installing ubuntu the raid set should be seen as a scsi devise, if its not seen then I most likely have a fakeraid and I should turn it off and use the software raid functionality.  is that correct?
Jose

---

