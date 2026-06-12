---
title: "Copy Windows recovery partition from a Dell Inspiron 1545 to another"
date: 2013-03-19
forum: Any Other OS
---

### Post by meijin3 on 2013-03-19
A while back I completely wiped my Dell Inspiron 1545 and installed Ubuntu on it, deleting all previous partitions including the Windows recovery partition. That was perfectly fine because I had no intention of using Windows any longer. Well, now I'm going to sell the thing and want to have Windows on it because I wouldn't dare try and sell it with an OS that most people in the market would not be using (not to mention, anyone who wants Ubuntu can easily install it themselves). Luckily for me, my aunt has the exact same laptop with Windows and the recovery partition intact! I was wondering what the easiest/most hassle-free method for copying just the recovery partition over would be.

My goal is to delete Ubuntu from the computer, copy over the Windows recovery partition, and then restore it to factory settings. I am so grateful for anyone who is willing to help.

---

### Post by mips on 2013-03-19
You can image it via dd or clonezilla. easy peasy!

---

### Post by meijin3 on 2013-03-19
I've never actually used Clonezilla and when I tried I wasn't sure I was using it right. I've looked for tutorials specifically on how to do this and nothing I found was helpful.

---

### Post by mips on 2013-03-19
The only thing you have to be very careful about is selecting the source and destination devices/partitions.

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)
[http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla](http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla)
[http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live](http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live)
[http://www.wikihow.com/Use-Clonezilla](http://www.wikihow.com/Use-Clonezilla)
[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

If I was you I would clone your aunts entire hard drive to yours and then delete the actual working windows partition you cloned and create a new one from the recovery partition.

---

### Post by meijin3 on 2013-03-19
Thanks mips, you've been a help to me in the past, and you're certainly one now.

---

