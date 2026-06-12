---
title: "md5sum question"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by paker on 2007-04-20
I see "ubuntu-7.04-desktop-amd64.iso" sitting on my desktop. But when I enter in the terminal "md5sum ubuntu-7.04-desktop-amd64.iso" it says the file does not exist. What wrong did I do? Thanks.

---

### Post by taurus on 2007-04-20
```
cd ~/Desktop
md5sum ubuntu-7.04-desktop-amd64.iso
```

---

### Post by paker on 2007-04-20
Thanks. Where can I find the reference number to compare md5sum result to? Thanks.

---

### Post by taurus on 2007-04-20
```

50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

```

---

### Post by Drakkor on 2007-04-20
Or what I have found out instead of actually typing the file name, just put in the terminal ```
md5sum
```  then just drag the .iso file into the terminal.........works everytime,lol   :)
Edit: it will take a little time for it to accomplish this, while it checks the file.

---

### Post by n3tfury on 2007-04-20
> **Drakkor said:**
> Or what I have found out instead of actually typing the file name, just put in the terminal ```
md5sum
```  then just drag the .iso file into the terminal.........works everytime,lol   :)
Edit: it will take a little time for it to accomplish this, while it checks the file.

nice tip! :D

---

### Post by paker on 2007-04-20
I have been a ubuntu user for a few months. One thing that frustrates me most is when I cannot locate the info that I know exists. I googled for "md5sum fiesty" but could not find the data. 

Taurus,
I don't know where you got the data. I thank you much.

---

### Post by taurus on 2007-04-20
I went to Ubuntu's site, clicked the download, went to mirrors, and picked one closest to me, and got the MD5SUMS from it.

---

### Post by Drakkor on 2007-04-20
oops

---

### Post by petersjm on 2007-04-21
I'm downloading the Feisty .iso now (after messing up my upgrade - I'm running Edgy's LiveCD now!). When I md5sum it, do I need the -c switch (or whatever it's called)? i.e. "md5sum -c kubuntu-7.04-desktop-i386.iso" (I think -c means "check"). Or do I not need to do this and just stick with "md5sum ubuntu-7.04-desktop-i386.iso"?

---

### Post by Drakkor on 2007-04-21
No -c needed
If you downloaded it to the desktop , you need to point the terminal there e.g. cd Desktop
As stated above , I like to just put: ```
md5sum
``` in the terminal, and then just drag the .iso file from where ever I downloaded it to , into the terminal, that way there's no typos, and I don't need to do alot of cd ing,lol :)

---

### Post by petersjm on 2007-04-21
Thanks, Drakkor. When it's fully downloaded (9 minutes and counting, from a torrent), I'll md5sum it and hope it's all fine. Thanks :D (I'm forever dragging files into the terminal, too - makes it all so much easier!)

---

### Post by petersjm on 2007-04-21
Damnit! Okay, the md5sum check worked and everything is okay. UNFORTUNATELY, I just realised I can't burn it to CD because I'm running off Edgy's LiveCD - which mean's there's a CD in the drive and it won't come out unless I shutdown. But in doing that, I won't be able to access /hda1 where I saved it to, because without the LiveCD I can't boot into Linux any more... Argh! Can anyone help???

---

### Post by Drakkor on 2007-04-21
(Krusty)  Aww Crap !!! ,lol
Can you put a straightened paper clip or something that small into the little hole in the cd drive to eject it ??

---

### Post by petersjm on 2007-04-21
Okay, I got it the LiveCD out by going to Nautilus and right-clicking for "eject". Put the blank CD in but then Edgy hangs - I guess because it's got no CD to run off anymore! Putts, I say!

Okay, I've had an idea. If I install Edgy from the LiveCD, can I put it on a smaller, new partition, so as not to overwrite the partitions I have? Then burn the iso to a new CD and install Feisty over hda1 and the new partition I just made? Will that work? I'm pretty sure my /home directory is on a separate partition but I'll check with gparted to make sure... God, this is turning into a nightmare! Thanks for all your help already, Drakkor.

---

### Post by Drakkor on 2007-04-21
Glad you got it out ok,lol , I just tried that while running a live CD , I tried to eject it with the paper clip, and the drawer came out with the disc spinning wildly !!! , and then I shoved it back in and it was making some really strange noises, lmao, but the drive seems to be ok , Lucky I have 2 drives,lol  :lolflag:

---

