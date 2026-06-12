---
title: "ext2 or ext3 for spare hard disk"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by peebly on 2007-08-31
Hello

I have a spare hard disk which I am going to use to store my mp3s.

Would there be any problems if I formated the new disk using the ext3 file system where I am going to store the mp3s.

Ubuntu is installed on another hard disk which uses ext2 I think, should I make them the same or does it not make a difference.

Also the lost and found folder what is it.

---

### Post by caclratm on 2007-08-31
I don't think you'll have any problems because the only difference (that I know of) between ext2 and ext3 is that the latter is journaled.

BTW, I would recommend instead to install ntfs-3g to be able to read/write to the ntfs filesystem. I have an external hdd myself that I use to store multimedia and it came in ntfs. I could read but I couldn't write so I just installed that driver and now it works just fine.

Hope that helps

---

### Post by ts51 on 2007-08-31
i don't think it makes a difference but what do i know

---

### Post by bodhi.zazen on 2007-08-31
You can use either but my advice is to go with ext3. ext3 is an ext2 with journaling which helps with data protection.

For informatio on the "Lost and found" file : [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

Ext2 : [http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

Ext3 : [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by peebly on 2007-08-31
Thanks people.:)

---

### Post by ts51 on 2007-08-31
no prob. 
 
sometimes i wonder if ubuntu is really easy to use or if this community is a made up of a thousand genisus. Especiially since I am only just 13 yrs. 
 
Heh, i got a dual boot and broadcom wirless to work... and I'm not that much of a geek :)

---

