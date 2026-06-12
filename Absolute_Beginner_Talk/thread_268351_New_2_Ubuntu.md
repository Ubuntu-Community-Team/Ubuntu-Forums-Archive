---
title: "New 2 Ubuntu"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by DarkChimera187 on 2006-09-30
Hi there everyone. I am new to Ubuntu Linux recently, mainly because my old PC's display card got fried and I had to move my old HD to the newer tower that I got from my uncle, and the drivers installed on the HD conflicted with the stuff that was in the new tower. I like the way Ubuntu is setup, easy to use, and uses less space than Windows. I would just like to know how (if at all) I could possibly speed up the OS so that it doesn't take 20+ minutes on to open OpenOffice.org. I used OO.org before but it had never taken that long to load pages. Anyway, if anyone can help me that would be awesome.

Here is what I know about the system specs.
```

1.8GHz Intel Celeron Processor
10GB Hard Drive (from a PC built in 1997)
128MB RAM
3D Intel Extreme Graphics AGP
```

Thanks in advance,
-DC](*,)

---

### Post by jr.gotti on 2006-09-30
Hmm...it appears that your system may be to old for Gnome to run to its fullest capabilities. Try using XFCE. (Download an Xubuntu ISO, or search for one of the many threads on how to convert your existing install)

---

### Post by K.Mandla on 2006-09-30
If it's taking 20 minutes to load OOo, then something is very wrong. :-k

Is this a full installation, or are you working off the live CD? Did you pick the default swap partition size? Any chances the hard drive is encountering errors? If it's from 1997, it's probably a 5400rpm or lower, right?

Just brainstorming.

---

### Post by DarkChimera187 on 2006-09-30
> **pixelPOET said:**
> Hmm...it appears that your system may be to old for Gnome to run to its fullest capabilities. Try using XFCE. (Download an Xubuntu ISO, or search for one of the many threads on how to convert your existing install)

Thanks, I probably will try that a little later.

> **K.Mandla said:**
> If it's taking 20 minutes to load OOo, then something is very wrong. :-k

Is this a full installation, or are you working off the live CD? Did you pick the default swap partition size? Any chances the hard drive is encountering errors? If it's from 1997, it's probably a 5400rpm or lower, right?

Just brainstorming.

No this is a full install. The Live CD took 3 hours to start the install. I went to a movie, came back and it was still loading, and I don't know how many RPM the HD is running. I'm not that smart about PC's. It was actually my friend who transfered the drive.

-DC ](*,)

---

### Post by K.Mandla on 2006-09-30
No problem. I'd have to side with pixelPOET in this case, then. I think it's possible the PC is running out of memory, and trying to work off the space on a hard drive. And if it's an old, slow hard drive, there's a very good chance transfer rates are compounding the problem.

I agree: Try installing Xubuntu; you can do it with *sudo aptitude install xubuntu-desktop* if you don't want to reinstall the entire business.

But to be honest, with performance that low, a reinstallation might be a fallback plan. :(

---

### Post by airtonix on 2006-09-30
> **DarkChimera187 said:**
> 
I would just like to know how (if at all) I could possibly speed up the OS so that it doesn't take 20+ minutes on to open OpenOffice.org. 
Here is what I know about the system specs.
```

1.8GHz Intel Celeron Processor
10GB Hard Drive (from a PC built in 1997)
128MB RAM
3D Intel Extreme Graphics AGP
```Thanks in advance,
-DC](*,)


Umm is it sdram or ddr ram.....not highly relevant, but would suggest getting at least 512mb of ram....

even windows doesnt; run properly with less than 512mb of ram

I chucked in a 1gb of ddr ram into my amd 1ghz box and it absolutley flys now....makes windows look ancient.

update: also i recommend getting a new harddrive....around my area (adelaide, australia) a 120gb harddrive typically goes for around 70 to 80 dollars.

and your video card is part of the motherboard no? this is also going to be aproblem if you want 3d acceleration.

well last time i tried it was but maybe its being fixed

---

### Post by Zyzzyx on 2006-09-30
Something seems screwy with performance that bad, can't quite place it though.

I've got a P3-500 that I installed Xubuntu (from the Server install CD). It has 128mb memory and an 80gb 7200rpm drive.

The initial install took awhile, but maybe just over an hour. 

Just for the helluvit I just swapped over to it (hooray for dual screens and KVMs). Ran *sudo aptitude update && sudo aptitude upgrade* first, that took a bit. Then went and ran *sudo aptitude install openoffice.org*, ya know, since I didn't have OO on there yet. ;) 

All of that took ~15 minutes. I can open OO and it comes up in about 15-20 seconds.



So, something seems up with your hardware. One thing to suspect is that your hard drive is dying, and is spending way, way too much time trying to correctly read/write information.

Another would be that something is screwy with your memory. Run *top* and copy over the first five lines. That'll at least let us take a look at some basics there.

---

