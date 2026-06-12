---
title: "PCPlus - Linux - NAS storage"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ianb_newbie on 2007-07-31
I've recently bought an old computer with a view to using it as NAS on my network, following an article in the PCPlus 257 MakeIt supplement.

Linux is safely installed (Ubuntu 6.06LTS - desktop, as recommended) and I think I've configured everything as per the article, but the computer doesn't appear on my (Windows) network as expected!

The steps I have taken:
1. installed Linux and partitioned disk as "/", swap and "/SRV" - to be the NAS partition.
2. installed Samba and amended smb.conf to contain my network domain name,
3. within the networking administration tools ensured the domain name is correct.

I think I've done all I should have - but the computer still does not appear on the network.

Have I missed anything obvious? I tried using the server version of Linux but didn't know how to change the domain name, hence the switch to the desktop version - which I'm using   now so the networking is working!

Help would be appreciated!

Ian B

---

### Post by mjwhitfield on 2007-07-31
First things first.  Are you able to ping the linux box from your windows box?

---

### Post by ianb_newbie on 2007-07-31
Hi mj,

No - pinging just times out! The IP address (handled by DCHP) seems to be fine and within the network range! Hmm! Just thought! Firewall - let me check that, too!

Ian B

---

### Post by mjwhitfield on 2007-07-31
you should assign it a static IP, much easier in the long run.

Check your firewalls and report back :)

---

### Post by ianb_newbie on 2007-07-31
I've been recommended FreeNAS ([www.freenas.org](www.freenas.org)) as an alternative and it worked! Very simple and no need for a full OS - and it's web-configurable.

So, now I'll get a big disk to replace this Compaq's 8Gb hard drive and my NAS will be working!

Thanks for the thoughts!

Ian B

---

### Post by mjwhitfield on 2007-07-31
I've looked at freenas before, however I wanted my samba server to be expandable, so I went the linux route.

---

### Post by ayenack on 2007-07-31
What do you mean by expanable?

In FreeNAS you can add new drives set raid arrays both hardware and software you can use USB drives & keys etc. Use many different network protocols SAMBA, CIF, NFS, FTP, and others. It's not a network solution as I'm sure you know but it does what it says on the tin and it does it well and for free. This sounds like I'm having a go I'm not and I hope it's not taken that way;):rolleyes:

ayenack.

---

