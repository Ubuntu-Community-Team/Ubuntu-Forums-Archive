---
title: "Applications/partition privileges"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by kulor on 2007-12-06
So yeah, I'm totally new to Linux, and it's kinda fun. :D
What I did, in order to be able to easily restore all my Windows programs without having to reinstall them in case something goes wrong with Windows, was make a larger partition and have everything install to that. It's worked out well so far, and I'd like to be able to have a similar setup in Linux in case something goes wrong there. Not that I have a choice, almost all my space was dished out to this partition, leaving a mere 8 GB to Ubuntu.
So basically, how do I get programs to install to a different directory than the default?

ALSO, as it would happen, this partition is set to read-only. I've tried chown and chmod, both of which denying me permission to perform said action if I run them without sudo, and both working for sudo if I did it with. I'd like for it to be automatically mounting, as opposed to me having to mount it every time...which it's doing, just in read-only apparently. Any other suggestions?

Thanks a bunch!

---

### Post by Brian Dempster on 2007-12-06
I just did almost the same thing and now I don't have permission to use the new disk.
I do not have permission to change permissions on the disk I just setup.
:confused:

---

### Post by banewman on 2007-12-06
Most progs automatically install to /usr/bin as default so a seperate partition for that is a choice.
To have a partition mount at boot you need an entry for it in the /etc/fstab file - what file system is the partition and where are you mounting it to?
:)

---

### Post by kulor on 2007-12-06
Thanks, banewman!
Now, would there be any way to change where /usr/bin is located?
As for the second question, I've got it mounting by itself right now, I just need to know how to make it writable, and some way I can do this that won't involve me manually re-mounting it with those privileges every time. It's a FAT32 drive, mounting to /media/hda7 (I think? I'm not in Linux right now, so I'll correct if it says otherwise)

---

### Post by banewman on 2007-12-06
There are tutorials for moving /home/you to another partition so the principle will be the same. In ubunu's home page is a link for tutorials - as a system file I'd only do it during an install though - but linux is free software. :)
What is the entry in /etc/fstab for the partition ?

---

### Post by kulor on 2007-12-06
I was having trouble finding said tutorials. Could you link to one please?
As for fstab: 
UUID=45DB-4D62  /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1

---

### Post by hyper_ch on 2007-12-06
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by kulor on 2007-12-06
Thanks, hyper_ch!
Well, I took the easy route and decided to reinstall, this time specifying the FAT32 partition as /usr. It didn't seem to like that very much...
"The file system type fat32 cannot be mounted on /usr, because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2."
Does this mean it's impossible to use my FAT32 drive for storing applications?

---

### Post by hogwartsnigel on 2007-12-06
Hi kulor,
I wouldn't bother moving the home directory..I succesfully did it a few weeks back. I would wait to do it on next install, and partition accordingly....have you worked out your permissions..I had the same deal and the "gksudo nautilus" in the command line helped me browse and permenantly alter all the r/rw options and ownership too self instead of root.

Hope that helps

Nigel

---

