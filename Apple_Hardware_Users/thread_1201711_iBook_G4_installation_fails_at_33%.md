---
title: "iBook G4 installation fails at 33%"
date: 2009-07-01
forum: Apple Hardware Users
---

### Post by cruising on 2009-07-01
Hello!

I'm trying to install Ubuntu 8.04 on an iBook G4 (with good specs, I believe. This is because I can't get any info about the laptop. It was already dead when it came). I used the Desktop Live CD put together by the community and it boots just fine. But when it gets the Hard Disk partitioning stage, it fails at 33% repeatedly. 

Can anyone please help?

Thnx

---

### Post by balt11t on 2009-07-02
You're going to have to supply more details. Is Mac OS installed? If it is you need to erase all partitions, create 2 or however many you need, one as Mac OS (Journaled) for Tiger, but you'll have to Google "suggested Mac OS partitions" for more information on that, and the other as free space. For Tiger you need to use the installation disc using utilities, Disk Utility. Then when installing, use the option "use largest fee space availible."
 
Hope this helps (if it doesn't, just post a reply and I'll try to help more.)
balt11t

---

### Post by cruising on 2009-07-05
> **balt11t said:**
> You're going to have to supply more details. Is Mac OS installed? If it is you need to erase all partitions, create 2 or however many you need, one as Mac OS (Journaled) for Tiger, but you'll have to Google "suggested Mac OS partitions" for more information on that, and the other as free space. For Tiger you need to use the installation disc using utilities, Disk Utility. Then when installing, use the option "use largest fee space availible."
 
Hope this helps (if it doesn't, just post a reply and I'll try to help more.)
balt11t

balt11t, 
Thanks for your response and great offer to help more with my predicament :) Okay, let me tell you a bit more about me. I'm fairly new to Ubuntu (about six months or so) and I've had problems in the past installing Ubuntu on both desktops and laptops, but figured them out or had help from people like you). I've never installed Ubuntu on a Mac before. The iBook I want to install Ubuntu on was ALREADY DEAD (would give you the chyme and a white-gray screen WHICH NEVER GOES AWAY. The owner, an American friend of mine who lives here n Ethiopia, had sent it to the US previously on three different occasions to have it repaired; only to keep getting the same problem over and over again.) So, you see I have absolutely no idea about the laptops specs and she doesn't either! I don't have anything 'Mac' to help me (she even had to buy a new charger). All I have is my precious CD images (it took me days to download them with the slow connection here) and guys like YOU!! So, what would be a great help to me is if I could find a way to do everything without ever having to ask help from anything "Mac". Ubuntu and internet connection only! 

Thank you so much and I truly appreciate the time and expertise you will put into solving this issue. 

I need this to work!

Cruising

---

### Post by tiresia on 2009-07-06
Did you try formatting the HD before starting the installation? Are you sure that the HD has no problem? Could you try with the Alternate Installer, or is it a problem to donwload it?

---

### Post by cruising on 2009-07-06
> **tiresia said:**
> Did you try formatting the HD before starting the installation? Are you sure that the HD has no problem? Could you try with the Alternate Installer, or is it a problem to donwload it?

Tiresia, 
Thanks for your interest! But can you actually format the iBook with the Ubuntu CD? I say this because the "Hard Disk formatting" option is somewhere in the middle and is dependent on the partitioning being done correctly, if I'm correct. Or if not, please let me know how to do it and I will definitely give it a try. As for the Alternate Installer, I have tried it with no luck either. Yes, downloading it is NOT easy. I takes days LITERALLY to download a CD image. Even downloading text is a problem here!

Thnx.

Cruising

---

### Post by tiresia on 2009-07-06
To format your HD, go to System>Administration>Partition Editor
Just try to format it as you like (I mean just choose ext3), the Installer will do it again because it needs to create other partitions.
I would like just to understand if there is any problem with the HD

---

