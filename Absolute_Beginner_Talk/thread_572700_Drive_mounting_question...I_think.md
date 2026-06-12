---
title: "Drive mounting question...I think?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-10
I have a network file server on my home network. While I have been able to navigate to it successfully I can't quite figure out if I have mounted it. I am wanting to use grsync to backup my home folder nightly. However when I browse in grsync to the destination I want to save to, it is not listed as a choice.

My file server is located at \\192.168.1.2\Disk-0\backup\ . I can use multiple platforms to access it (smb, nfs, ftp, http, rsync).  Any help is appreciated, i have been looking around but haven't found it yet.

---

### Post by finer recliner on 2007-10-10
anything currently mounted will appear in /etc/mtab

this file is generating automatically. do not edit it yourself.

---

### Post by mramsey on 2007-10-10
I have tried using Smb4k and get this error(see Screenshot). ???

---

### Post by mramsey on 2007-10-10
Ahaa! I reached that pivotal moment when it just all makes sense cause the lights came on.:lolflag: Smb4k is my new friend for now. I can now access all of my stuff on the NAS through all of the apps.

One happy camper here!):P

---

