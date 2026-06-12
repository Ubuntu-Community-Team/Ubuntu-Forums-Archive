---
title: "Windows Client sign in password not working on NFS +1 more problem"
date: 2020-12-01
forum: Apple Hardware Users
---

### Post by cmpx23 on 2020-12-01
I'm a total newb when it comes to Linux and NFS, double trouble I feel.... I had plenty of help to get me this far. I have mounted 2 external HDs to my Linux and shared one via Samba (mac external) and PC external via NFS. I can sign into the samba (PC External) from my mac just fine but when I go to my PC laptop (windows 10) I cannot sign in, it will not accept my password. I cannot understand where the break down is, anyone ever heard of that problem? I have tried google searching and not found one thing about it.

Now second problem, the Samba Mac External, I can see (read it) it from both the iMac and PC Laptop (windows 10) but I cannot seem to write to it, I have set it up in /etc and should be able to write to it but when I try to -l it doesnt show it green highlighted drive.

---

### Post by TheFu on 2020-12-02
These forums have 10+ threads about connecting win10 to ubuntu samba. search. There were changes to win10 that broke lookups and changed defaults.  The version of ubuntu could matter for the answer.

I don't know anything recent about apple stuff.

---

### Post by cmpx23 on 2020-12-02
I figured it out, I was following some steps to mount the shared drive and it had some wrong commands, it took me about 30 minutes but I did eventually figured it out. 

I am still trying to figure out the read write permissions to the macos formatted external HD, I can see the drive and read but cannot write. I'm not sure if I have to do something the client sides or the host side.

---

### Post by TheFu on 2020-12-02
> **cmpx23 said:**
> I figured it out, I was following some steps to mount the shared drive and it had some wrong commands, it took me about 30 minutes but I did eventually figured it out. 

I am still trying to figure out the read write permissions to the macos formatted external HD, I can see the drive and read but cannot write. I'm not sure if I have to do something the client sides or the host side.

Glad you did.  With the information provided, nobody here could help you.  We need details - like what, exactly, you did. Which OS release? Most importantly, we need to see the config files.  If you used some GUI, say that. Usually the best, fastest, methods for file sharing over a network require manual text config file setup.

As for accessing non-Linux file systems, that's a completely different issue. You'll find more help in Apple specific forums, I'd bet.  If the file system isn't a native linux file system (ext3/4/2, xfs, zfs, f2fs, jfs, or any of the 50 other options) like exfat, ntfs, hpfs, then hacked together drivers are needed and those are often buggy and lacking capabilities. They almost never support the Unix permissions model, which means some workaround is needed.  When support is really new, often the developers will not support read-write operations because they don't want to corrupt data.

---

### Post by wildmanne39 on 2020-12-02
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

