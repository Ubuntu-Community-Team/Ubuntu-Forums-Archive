---
title: "Why have an ubuntu Server system running?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by da Wookiee on 2008-01-08
I"ve been curious about having a Ubuntu server running, but am not sure what I would do with one if I had one.


I've got my current system that I'm using as my primary system currently, excerpts from the hardinfo report below

Computer
Summary
Computer
Processor	AMD Athlon(tm) 64 Processor 3000+
Memory	2075MB (315MB used)
Operating System	Ubuntu 7.10

Display
Resolution	1280x1024 pixels
OpenGL Renderer	GeForce 7100 GS/PCI/SSE2/3DNOW!
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	NFORCE - NVidia CK804

It currently has a 12 gig / partition and a 120 gig /home partition.  

I'm probably going to retire it when I get a laptop later this year.  What I guess I want to do is have a server that could store backup images for both a  laptop that dual boots Ubuntu/XP and a  MythTV backend.  I'd also like to have a folder that both computers could download to and read from so that it wouldn't matter which computer it downloaded on, either could access it.  It that what a server would do and is that the best way to go about it?

---

### Post by gate on 2008-01-09
yes, a server can do that.


  The thing you probably want to use is Samba, which allows a windows network drive and a Linux Network File System to all accesses the same space. I haven't done this myself as it is more than I need, but I use it at work where we have a Linux/OSX/Windows enviroment that all share user home directories on a network drive using Samba for Windows and NFS for Linux. 
  

   What I have set up is a box that is always on that acts as a web/database/fileserver. It is Ubuntu 7.10 and I have it set up so that all downloads of major files happen on the server, then I use scp or winSCP to transfer those files when I need them, or use USB drives if the files are really big. It acts as a central backup and file repository. 


   You should decide how much time/effort you are willing to spend and look at Samba, but the only reason to use it is to integrate XP into the situation :)

---

### Post by Paqman on 2008-01-09
> **da Wookiee said:**
> I'd also like to have a folder that both computers could download to and read from so that it wouldn't matter which computer it downloaded on, either could access it.  It that what a server would do and is that the best way to go about it?

That's a concept called Network Attached Storage. You can buy a NAS off the shelf, or you can turn a PC into one like you're talking about doing.

I put a NAS on my home network recently. We no longer store any data on the other machines. All our pictures, music, etc is on the NAS, which has two hard drives mirroring each other (a RAID 1 array) to protect against a drive failure causing data loss.

I'd recommend doing the same to anyone with multiple PCs and data they want to safeguard.

---

### Post by shareMenaPeace on 2008-01-09
Paqman, do you encrypt those data?

---

### Post by Paqman on 2008-01-09
Nope, can't say it's ever occurred to me that I should. Why do you ask?

---

### Post by shareMenaPeace on 2008-01-09
Just out of couriosity actually, i just read also a topic about this in the cafe forum, maybe thats why.

Well i never crypted yet but if its easy i would do this for personal informations, but basicly i dont care - lets say i got used to it - i even belive my home is full of devices monitoring me 24h LOL :D

Cheers

---

### Post by hyper_ch on 2008-01-09
> **Paqman said:**
> That's a concept called Network Attached Storage. You can buy a NAS off the shelf, or you can turn a PC into one like you're talking about doing.
You don't need to buy one... you can just mount it in your linux filesystem and on windows use samba to attach it as network drive.

---

### Post by Paqman on 2008-01-09
> **shareMenaPeace said:**
> Just out of couriosity actually, i just read also a topic about this in the cafe forum, maybe thats why.


Fair enough. I'm pretty happy that my home network is relatively secure (including wifi). It's just personal info anyway.

---

### Post by da Wookiee on 2008-01-09
> **gate said:**
> yes, a server can do that.
     You should decide how much time/effort you are willing to spend and look at Samba, but the only reason to use it is to integrate XP into the situation :)

I had planned on using Ubuntu and Samba.  Are there any good howtos on how to set it up that you could point me too?

---

