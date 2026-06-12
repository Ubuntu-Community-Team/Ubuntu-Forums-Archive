---
title: "reading HFS+ volumes and iPod"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by liberalist on 2008-03-24
Hi everyone,

I have looked through the forums, but couldn't really find a solution tailored to Kubuntu. My problem is related to volume formatting, specifically the HFS+ format. In Ubuntu, I could read HFS+ (Apple/Mac formatted) volumes out-of-the-box. However - in Kubuntu 7.10 - I get the following error: ```
hal-storage-fixed-mount-all-options refused uid 1000
```

I have installed hfsplus and libhfsp0. How can I read my Mac OS X volume and iPod nano volume (which is HFS+ formatted as well) in Kubuntu? Moreover, when Kubuntu is able to read HFS+ volumes, how can I get my iPod to work with Amarok? 

Thank you very much in advance. 

PS: Read and write support would be nice, but is not required.

---

### Post by cyberdork33 on 2008-03-24
since this is a kernel level function, I don't really understand why it is different for Kubuntu. You might try asking in a kubuntu/KDE specific forum since it is likely something specific to that

---

### Post by liberalist on 2008-03-26
I have posted my problem at the [Kubuntuforums]("http://kubuntuforums.net/forums/index.php?topic=3092633.0"). While I am waiting for an answer, I have found a work-around in [this thread]("http://ubuntuforums.org/showthread.php?t=612901"). Apparently, I need to open Dolphin as root and then I am able to access Mac OS X volumes (or other HFS+ formatted drives). 

So it is a permission problem. However, this sounds like a bug to me. Do you know if this problem is going to be fixed in Kubuntu?

---

### Post by cyberdork33 on 2008-03-26
It is probably actually not a bug... HFS+ supports unix-style permissions and Linux, of course, respects the set permissions on such filesystems. Your OSX user is likely attributed as the "owner" of the files and folders on your iPod, and thus, your Ubutnu user is limited as to what can be seen, modified, etc. The root user can bypass those permissions (because it's root!) so it works like you want it to.

The thread you linked to implies though that Kubuntu may be mounting the drive incorrectly and could be the cause of the problem.

---

