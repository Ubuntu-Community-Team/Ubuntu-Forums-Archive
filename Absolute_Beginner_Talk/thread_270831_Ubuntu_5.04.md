---
title: "Ubuntu 5.04"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by kwlam on 2006-10-03
I have installed ubuntu 5.04. I have several problems.
1. I cannot find my windows partition. I cannot find it in /mnt/ or /media. How to mount it (preferrably with GUI) and mount automatically on starting the computer?
2. I cannot play vcd with totem. I follow the documentation already. There is error.
3. I cannot play mp3 with rhythmbox. Also, I cannot play the mp3 on ipod with rhythmbox.
Please kindly help me.

---

### Post by Albi on 2006-10-03
> **kwlam said:**
> I have installed ubuntu 5.04. I have several problems.
1. I cannot find my windows partition. I cannot find it in /mnt/ or /media. How to mount it (preferrably with GUI) and mount automatically on starting the computer?
2. I cannot play vcd with totem. I follow the documentation already. There is error.
3. I cannot play mp3 with rhythmbox. Also, I cannot play the mp3 on ipod with rhythmbox.
Please kindly help me.

Why not get dapper?

Anyways,

1) Do the command sudo mount -t ntfs /dev/hda1 /windows -o nls=utf8,umask=0222

And it should appear under the folder windows (I'm assuming it's an NTFS partition)

2/3) Get Automatic (getautomatix.com) and install the non-free codecs.

---

### Post by kwlam on 2006-10-03
Thanks.

I am using windows 98. Should it be vfat rather than ntfs?
Is it necessary to edit the fstab if I want it to be mount automatically?

Also, it ubuntu 6, is the windows partition mounted automatically?

---

### Post by comppsyco on 2006-10-03
The windows partition is not mounted automatically, but it's pretty easy to do. [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) will tell you how. And yes, win98 should be vfat, unless I'm mistaken.

---

### Post by kwlam on 2006-10-04
Thank you. I have install the diskmounter and it is OK.
However, I cannot download the automatix. I am using computer in my office and it is blocked by firewall, I think. I can only use http and no other, not even ftp or get. Can I download some package so that I can install the codec. Also I previously mandrake and so I use rpm. In ubuntu, what can I use? Is it deb. How to use it, with synaptic package manager or what else? Can you show me the documentation?

---

