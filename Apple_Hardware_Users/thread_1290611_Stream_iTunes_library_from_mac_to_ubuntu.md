---
title: "Stream iTunes library from mac to ubuntu"
date: 2009-10-13
forum: Apple Hardware Users
---

### Post by XingZ on 2009-10-13
Hey guys. I'm trying to set up my mac and ubuntu so that I can listen to my iTunes library that's on my mac in ubuntu. I'm using my universitys internal wireless network. So I think loopback connections are blocked so I can't ssh or FTP.  So I'm trying to set up smb from mac and ubuntu.  

Any suggestions as how I should proceed?

Thanks in advance.

---

### Post by Rem0te C0ntr01 on 2009-10-14
Hi XingZ,

This shouldn't be to hard to set up at all. I helped my brother with a similar set up, although he wanted to store the music on his ubuntu server and reference his itunes library on his mac to that folder. It is working really well for him. All you should have to do it set your itunes music folder as an smb share. Then hop on your Ubuntu machine and see if you can browse to the share from Places -> Network.
If you can't find it, you can mount it from Places -> Connect to Server.
If you run into any issues let me know, and I will see if I can help. If this is a public wifi network this could pose a security risk as others may be able to access this share as well-just fyi

---

### Post by ReddogOne on 2009-10-14
Rhythmbox will do this all for you. Just turn on DAAP (I think that's the feature) and you can then share libraries between iTunes and RB.

---

### Post by Joeb454 on 2009-10-14
> **ReddogOne said:**
> Rhythmbox will do this all for you. Just turn on DAAP (I think that's the feature) and you can then share libraries between iTunes and RB.

This does indeed work very well. I have a similar set up at home. Though it did confuse me at first, when I saw my Rhythmbox shared library in iTunes ;)

---

### Post by XingZ on 2009-10-14
Thanks for the quick replies guys.
Still having trouble with connecting between the two computers.

I've set up mac (snow leopard) with file sharing, and it returns a address smb://...  Then when I go to ubuntu to connect via nautilus's Go To Location "smb://..." I failed to retrieve share list from server.

When I browse through smb on ubuntu via smb:///, the only group I can access is WORKGROUP, which contains only my computer's sharename.

What didn't I set up correctly?

Also, should I be able to access my ubuntu computer via mac if I were to setup this correctly?

Thanks again.

---

