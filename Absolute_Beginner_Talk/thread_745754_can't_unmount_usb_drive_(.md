---
title: "can't unmount usb drive :("
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2008-04-04
i just got this usb drive like 2 hours ago because my last one broke i think because i pulled it out before i unmounted it once, so this is crutial lol i just popped it in and it automatically mounted to /media/disk-1 and then i did what i needed to and after about 5 minutes tried to unmount it and it said it was busy.. so i closed everything and it still didn't work
then i read online and i've cd to my home directory adn tried it and did that fuser command and it says nothing is using it... so for the love of god can someone please help me eject this safely. thanks in advance

p.s. this is what im getting when i try to unmount it

spencer@spencerUBUNTU:/$ sudo umount /media/disk-1
umount: /media/disk-1: device is busy
umount: /media/disk-1: device is busy

---

### Post by bred on 2008-04-04
> **onearmedpanda said:**
> i just got this usb drive like 2 hours ago because my last one broke i think because i pulled it out before i unmounted it once, so this is crutial lol i just popped it in and it automatically mounted to /media/disk-1 and then i did what i needed to and after about 5 minutes tried to unmount it and it said it was busy.. so i closed everything and it still didn't work
then i read online and i've cd to my home directory adn tried it and did that fuser command and it says nothing is using it... so for the love of god can someone please help me eject this safely. thanks in advance

p.s. this is what im getting when i try to unmount it

spencer@spencerUBUNTU:/$ sudo umount /media/disk-1
umount: /media/disk-1: device is busy
umount: /media/disk-1: device is busy

[COLOR="Blue"]do u have win xp or vista? I had the same problem, I puled my usb external HHD and forgot to unmount it, so my solution was to check the HHD for errors from windows and to remove/unmount correctly from windows - than it worked on ubuntu...hope it helps[/COLOR]

---

