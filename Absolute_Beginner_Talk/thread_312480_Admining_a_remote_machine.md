---
title: "Admining a remote machine"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-12-04
Hi, I've been admining a remote debian box from windows using putty.exe.

Now that I'm (slowly) transitioning over to ubuntu, I'm looking for a better way to do this other than opening a terminal.  I'm hoping this will accomplish two things, one help me become more efficient at administering the box, and two, help me become a more proficient linux user.


Some basic questions:
- Are there ways to mount a remote drive?  What are the benefits/dangers if so?  

- Can I make a symlink to a remote drive?  Again, if I can, do I want to?

- Can I use any of the above methods to help me back the remote machine up to my local machine?


I'm hoping to make a script to back up the remote machine to my local machine, and then take that backup and burn it to some removable media.  

Primarily, I'd just like to get a back up to the local drive first, and worry about getting fancy later.

---

### Post by Bachstelze on 2006-12-04
NFS is what you're loking for, search the Wiki for it :)

---

### Post by the gnome on 2006-12-04
Cool thanks!  You steered me to quite a bit of reading! :o :-D

---

### Post by IYY on 2006-12-04
If both machines are running Linux, everything you are trying to do is incredibly easy. 

The instructions I used are right here: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

And yes, you can link to them, and writing shell scripts for backups is very easy too.

---

### Post by the gnome on 2006-12-04
Thanks for the tip!  After some initial research, I got excited about using NFS for my remote backups, but after a little more reading I got worried about using NFS over the internet for security reasons.

The discussions at the bottom of this article specifically talk about security:
[http://linuxdevcenter.com/pub/a/linux/2003/03/06/nfs_backup.html](http://linuxdevcenter.com/pub/a/linux/2003/03/06/nfs_backup.html)

I'm starting to look into rdiff for my backups which will let me use ssh for my backups:
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

### Post by keeb on 2006-12-04
For backups, consider using Mondo. Very good tool... will back your server up directly to removable media, in fact!

---

