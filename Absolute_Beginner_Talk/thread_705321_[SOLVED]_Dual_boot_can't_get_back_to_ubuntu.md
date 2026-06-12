---
title: "[SOLVED] Dual boot can't get back to ubuntu"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by vpik01 on 2008-02-23
Stupid question I'm sure but here it goes; I wiped XP Tablet edition from my Thinkpad x41 Tablet and successfully installed  Ubuntu 7.10 last week and have been working through getting the tablet functionality working. In the mean time I installed Vista in the unpartitioned space I left when I installed Ubuntu...

Now I can't get back into Ubuntu, the system boots right into Vista without any opportunity to select Ubuntu... any help? Thanks!

---

### Post by glennric on 2008-02-23
Check out the following link:
[Recovering grub after installing windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Duck2006 on 2008-02-23
Or you can try this boot loader to boot ubuntu.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by vpik01 on 2008-02-23
Thanks for the response!

I followed the instructions on the 'Recovering Ubuntu after installing windows' and it seems to have worked. I had to play around with the hd(0,1 2 3) untill I found that windows was installed on hd(0,3).

Now I have to try and combine my Fat32 partition that was going to be for file storage and use by both ubuntu and vista and add it to the vista partition... honestly 7 gigs and I can't even complete windows update without running out of space?!?  

I'm not sure but I think I will end up having to delete both the vista and fat32 partition, re-make them in ubuntu and reinstall vista... which isn't too bad just time consuming.

---

### Post by northern lights on 2008-02-23
Gutsy reads and writes on NTFS fine - no need for FAT whatsoever.

Maybe it ain't that simple, and it's not the way you're trying it, but in case you are attempting to just combine the partitions first hand - I'd say you wanna erase the FAT partition and then simply extend the NTFS (Vista) one into the newly created unallocated space.

---

### Post by vpik01 on 2008-02-23
Really?!?  Thats great, and news to me... I'll give it a try!

---

