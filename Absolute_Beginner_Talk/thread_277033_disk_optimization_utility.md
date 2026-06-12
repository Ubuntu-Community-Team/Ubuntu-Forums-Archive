---
title: "disk optimization utility"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-10-13
what's the best disk defragmenter for linux?

---

### Post by raqball on 2006-10-13
You **DO NOT** need to defragment Linux.... It's not Windows :)

---

### Post by Frak on 2006-10-13
> **raqball said:**
> You **DO NOT** need to defragment Linux.... It's not Windows :)
raqball's got a serious point.

---

### Post by dannyboy79 on 2006-10-13
> **raqball said:**
> You **DO NOT** need to defragment Linux.... It's not Windows :)
There's no need to get like that! you simply could have told him that the filesystem Linux uses most of the time is ext3 and that doesn't need to be defraged. whereas ntfs and fat32 do.

---

### Post by raqball on 2006-10-13
No need to get like what? Did you NOT see the smiley face? My post was short and to the point with a SMILEY face at the end.... Sheesh... I can bail on this board if that's how other are here.....

Thanks and have a great day :) (see the smiley face)?????????????????????

---

### Post by emarkay on 2006-10-13
May I, as a noob, ask why???  I know the FAT wastes space and the placement of files in not consecutive, but why is Linux better, technically?   :)

---

### Post by xXx 0wn3d xXx on 2006-10-13
> **emarkay said:**
> May I, as a noob, ask why???  I know the FAT wastes space and the placement of files in not consecutive, but why is Linux better, technically?   :)

Linux filesystems are designed to resist fragmentation. Your filesystem is checked at every boot for too much fragmentation and if there is, it is fixed. It is also checked for problems after 30 boots and fixed.

---

### Post by raqball on 2006-10-13
Good post! Also, If I may, ext3 tends to write in 'continuous space' as opposed to NTFS / FAGT32 that writes to '1st available'.... :)

---

### Post by gvgerman on 2006-10-13
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by emarkay on 2006-10-14
Way cool!  Thanks for the info!  :)

---

### Post by mokmoki on 2006-10-26
wow... neat replies... thanks guys, that's one more to my list of pros for linux. way to go linux users! :)

---

### Post by jdong on 2006-10-26
If you search up "pyfragtools", I have actually written a Linux defragger, but it's largely pointless unless you do very specific kinds of work (huge and slow torrents of data that needs to be read back fast... which I can't think of too many examples of)

If you're looking for running it like a Windows disk optimizer equivalent, don't bother... I tried it on a 6-month-old ext3 partition, and timed several common activities (from bootup to app loading) before & after 10 defrag passes. No difference whatsoever.

---

