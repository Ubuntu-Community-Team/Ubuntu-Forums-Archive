---
title: "Way for seamless read/write access between shared Windows and Linux harddisks?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by youtin on 2008-02-25
I have multiple partitions just for data and I was wondering if there is a way (such as a specific format) to use them from both Linux and Windows seamlessly. There was a post here suggesting using FAT32, but since it's dated 2005, I was wondering if there's any update regarding this. My largest partition is about 100GB. I would like my bittorrent client and other programs to write to the partition directly, which would later be usable from XP as well.

Any insight is much appreciated :)

---

### Post by mikewhatever on 2008-02-25
Today, it does not matter which format to use, because Linux can write to NTFS with ntfs-3g just as well as Windows to ext3 with fs-driver. FAT32 is writable by both OSs by default. In order to have full access to your storage partitions, they'd have to be mounted properly:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)
Let me stress it again, mounting permissions are the key here and not file systems.

---

### Post by youtin on 2008-02-25
I tried it and it seems that it works. (I haven't booted into Windows yet to check if it works from that side). But so far so good. Thanks a lot! :)

---

### Post by mikewhatever on 2008-02-25
> **youtin said:**
> I tried it and it seems that it works. (I haven't booted into Windows yet to check if it works from that side). But so far so good. Thanks a lot! :)

Check out [fs-driver homepage]("http://www.fs-driver.org/") if you haven't yet, that's in case you are going to use ext3.

---

