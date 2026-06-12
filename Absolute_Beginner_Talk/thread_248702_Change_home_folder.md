---
title: "Change home folder"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Flavian on 2006-09-01
This is kind of a newbie question :D but that's what the newbie board is here for, eh?
I have an ext3 partition, 1 NTFS and 1 FAT32 partition, the Fat32 part. is my stuff harddrive and I was thinking about moving the home folder to the Fat32 partition, in order to share it in windows as well.
How do I do that PERMANENTALLY.
Question: will [Desktop] be in there as well?
And will things I save in the future be saved on the Fat32 partition as well?
Thanks in advance

Flo

---

### Post by pbaehr on 2006-09-01
Well, here's the story. I'm including a link at the bottom which explains how to move /home to its own partition. This is a nice idea because it adds a layer of protection between the OS and the /home directory so that, for example, you could reload the OS without worrying about losing your data.

HOWEVER,
If you move /home to a FAT32 partition certain features like file permissions can not be written. I'm not sure what degree of breaking this will cause on your system, but I would strongly recommend against it. I've also heard there can be problems sharing information with Windows in this manner. I would not put your /home directory on the FAT32 partition. If you want to experiment with sharing a FAT32 partition, I'd try it by mounting a new FAT32 partition and considering it shared between the two operating systems.

If you decide you want to move your /home directory (though, again, I would strongly recommend against moving it to FAT32) here is the method:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Oh, and if it suits you, here is a link to a driver which will allow Windows to read ext2 and ext3 partitions:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

---

