---
title: "[SOLVED] How do I enable swap partition at start up?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by vvvladut on 2008-02-09
I resized my primary Ubuntu ext3 partition and took some space from my Windows ntfs partition; in the process my swap partition which sits in between them got moved. Now in Gparted I see that it is disabled, although it appears in my /etc/fstab. 

How do I make it to be enabled at start up?

Thanks!

---

### Post by PmDematagoda on 2008-02-09
Post the outputs of:-
```
blkid
```
and
```
cat /etc/fstab
```

---

### Post by tyggna1 on 2008-02-09
you can also just run
```
swapon /dev/hdx
``` to turn on the swap file.  If fstab won't use it right, then you can just go to sessions and add that command to your startup programs.
check out man swapon for more detailed info.

---

### Post by cdtech on 2008-02-09
> **vvvladut said:**
> I resized my primary Ubuntu ext3 partition and took some space from my Windows ntfs partition; in the process my swap partition which sits in between them got moved. Now in Gparted I see that it is disabled, although it appears in my /etc/fstab. 

How do I make it to be enabled at start up?

Thanks!

By using the command line blkid you will see your block id for the swap partition. Change the block id on the swap section in your /etc/fstab file like mine is shown here:
```
# /dev/sdb5
UUID=895c93de-63d5-468f-99b7-d0f70696928b        none            swap    sw     0       0

```
Normally /dev/sda# or /dev/hda# is fine in /etc/fstab. However, Ubuntu prefers using the blkid number, I'm not sure why.

---

### Post by vvvladut on 2008-02-09
I used blkid, copied the UUID number and pasted it in my /etc/fstab. And...it worked! I restarted and my swap partition is on! Thanks!

---

### Post by coolnezz on 2008-06-02
it worked for me too!  i reformatted my swap space a couple months ago and since then it wouldn't turn on at boot up.
used blkid
then followed CDTECH's sample, it worked!
been using Linux since January '08, still learning everyday.

---

