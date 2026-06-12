---
title: "Write to HFS+ and Set Permissions for Mac HD"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by underoathmatt on 2009-10-29
I just got Ubuntu 9.10 KArmic Koala running on my MacBook Pro.  Is there a way to get my computer to be able to write to HFS+ and is there a way to change my permissions to be able to access all of the documents on my Macintosh HD partition? It won't allow my to access certain folders such as /Users/(My Name)/Music.

Thanks.

---

### Post by besweeet on 2009-10-29
I'd like to know the answer to this as well. Was going to play with F-Spot but I couldn't get into my Pictures folder.

---

### Post by spencercarran on 2009-10-29
I normally just transfer all my files over with an external HD, or else you could use an online synchronization service like Ubuntu One. I'm not sure of the status of HFS+ support in Linux, but I don't think it works very well. You could try having a shared storage partition between them in FAT32, but that's a bit of a kludge.

---

### Post by Silmathoron on 2009-10-30
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
+ for mac, set usermode to 501
> sudo usermod -u 501 username

---

