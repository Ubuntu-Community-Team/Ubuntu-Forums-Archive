---
title: "vista won't give me a big enough partition"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by beckym@cincoed on 2008-04-02
I'm about to install ubuntu onto my pc. having read lots of threads on the fact that vista isnt happy if its partition is resized by anything else (and having learned the hard way that Vista MUST be boss or it just won't play ball), i have tried to shrink the vista partition using its own disk management tool. 

My C drive has 111gb free space (36.1gb used) - i have defragmented the drive - but vista will only shrink down from 151g  to 107g - leaving me with 44g for ubuntu - the thing is i want to give the majority to ubuntu because i want to use it most of the time but i can't seem to get vista to give me any more space. Has anybody got any ideas?

also, once i've shrunk it down, i was thinking of creating the new partition using ubuntu liveCd - is that a good idea and will ubuntu be happy?  any ideas very much appreciated :)

---

### Post by sayakb on 2008-04-02
Leave the 44GB unformatted. Create an ext3 partition using the Live CD.. leave a good amount of space as swap. I have given Ubuntu 20GiB and the rest of the space on my HDD to /home.. Out of 20, I have 12GiB free even after installing the basic packages + netbeans + vmware + KDE4 desktop + XFCE4 + IceWM .. :) :)

---

### Post by beckym@cincoed on 2008-04-02
Ok, so i should be fine with 44gb. how should i format the 'swap' space? fat 32? and will i be able to automatically access that from both vista and ubuntu (or am i misunderstanding what you mean by 'swap'?)

---

### Post by sayakb on 2008-04-02
> **beckym@cincoed said:**
> Ok, so i should be fine with 44gb. how should i format the 'swap' space? fat 32? and will i be able to automatically access that from both vista and ubuntu (or am i misunderstanding what you mean by 'swap'?)

 AT the LIveCD partitioner, create a new partition with Filesystem swap (Check the drop-menu which has ext3 by default). Also, after you create an ext3 partition, you have to edit the partition to chose a Mountpoint as "/" for the main ext3 partition.

---

### Post by frezasaga on 2008-04-02
maybe it better to use third party software to resize a HDD partition like acronis.........sometimes it solve my problem a lot......

---

### Post by housam on 2008-04-02
The Gparted tool is good enough for this job, either from the ubuntu live CD ( system >> admins. >> partition editor ) or from Gparted live cd ( downloading , burning to a cd and boot from it )

---

