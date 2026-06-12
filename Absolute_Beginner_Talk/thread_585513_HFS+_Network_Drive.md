---
title: "HFS+ Network Drive"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by spitfire915 on 2007-10-21
I am currently a new Ubuntu user and have one quick question to ask someone who knows what they are doing.

My setup:
iBook G4 1.33 GHz with HFS+ Western Digital External Hard Drive (non-Journaled)
Intel Pentium II MMX 400 MHz running Ubuntu 7.04 (Feisty Fawn)

Currently, the Pentium II is going to be set up to host a small client-based server. Right now, the WD drive is hooked up to my iBook and cannot be moved from that location. What I need to do is mount the WD drive on my Ubuntu computer with read/write capabilities across my network. I have a static IP on my iBook if that helps. Also, I have two Linksys routers piggybacked and my iBook is on the main router and the Ubuntu computer is on the piggybacked router. Both can connect to the internet so I don't see why that would make a difference, but it did with my Xbox 360.

---

### Post by HermanAB on 2007-10-21
Well, to share the external drive, you need to run a server on the Mac.  Linux and Mac can all run the same network systems, so you have to pick one you like:
a. FTP
b. SSH
c. SMB
d. NFS

Then you have to ensure that the two machines have the same network settings and are on the same subnet, open the firewalls for the chosen protocol, run the chosen server on the Mac and connect from Ubuntu.

So, pick a system and ask some more pertinent questions later.

Cheers,

Herman

---

### Post by spitfire915 on 2007-10-23
Ok... I have my Mac running an FTP server. I can connect to my internal HD fine, but I still need to connect to my external HD. The external is plugged into a USB hub which is plugged into my computer. For some reason, I cannot mount the external HD on my ubuntu comp. I have all the BSD names if you need them... the external HD is disk1 and the HFS+ partition on it is disk1s3. I need to mount the HFS+ partition across the network onto my ubuntu comp.

---

