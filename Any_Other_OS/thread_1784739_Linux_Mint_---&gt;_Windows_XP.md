---
title: "Linux Mint ---&gt; Windows XP"
date: 2011-06-17
forum: Any Other OS
---

### Post by Th3Blaze on 2011-06-17
Any help ? main partion is ext3 which windows should be able to read but it's saying its invalid.
Thanks In Advance !

---

### Post by arubislander on 2011-06-17
AFAIK Windows is not able to read ext3 without any additional software installed.

---

### Post by Th3Blaze on 2011-06-17
Ah, Im trying to get it to fat or ntfs, but if I change partions it delete the file system. Ive made a gParted live cd and obviously a Windows CD.
So what do I do next ?

---

### Post by fballem on 2011-06-17
As far as I know, Windows does not come with native support for ext3 drives/partitions. Linux can read / write NTFS drives / partitions, but not the other way around.

This link may provide a solution to your problem: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Hope this helps,

---

### Post by mips on 2011-06-17
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by Th3Blaze on 2011-06-17
Sorry , doesn't help at all. It says I need Windows. Im trying to change me OS from Linux to Windows.
I mean how do I boot the GParted CD to make a partion ?
After I have changed the partion.
It is as confusing for me as it is for you.

If I change the partion, it warns me everything will be deleted. So I can't do anything. Cant make cd's get stuff ect.

---

### Post by jeffathehutt on 2011-06-17
As far as I know, you cannot change the filesystem from ext3 to ntfs.  You would have to reformat to do that, and as you stated you would lose all data on the partition.  The only option I know of is to back everything up, then reinstall Windows.

---

### Post by Th3Blaze on 2011-06-17
Reinstall ? Never had it in the first place ?

---

### Post by jeffathehutt on 2011-06-17
What exactly are you trying to do?  I'm still not sure I completely understand.

---

### Post by Th3Blaze on 2011-06-17
Install Windows XP.
To do this I need to make a fat or ntfs partion.
If I do this, it deletes my firmware.
I need to have something booted on a CD to make a partion

---

### Post by pricetech on 2011-06-17
In order to make the partition, or make space for the partition, you will have to remove or shrink the partition you have.

You need to back up your data before you make any changes so you don't lose your data.

You may have to reinstall your current OS, which you indicate is mint, after you shrink the partition.

You don't say what you need XP for.  You might have other options depending on what you plan to do with XP.

By the way, your XP is licensed, right ???

---

