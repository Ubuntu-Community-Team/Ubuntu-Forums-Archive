---
title: "Backing up home directory"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-10-17
Had I known better when initially installing Ubuntu I would have put my home direcotory on its own partition.  But I didn't and now that I have everything just so I would hate to have to start over if tragedy struck and I had to reinstall.  So....

How can I back up my home directory?

If I can do this successfully and had to do a fresh reinstall is it correct to say that using my backed up home directory would restore everything exactly as it is now?


And one more, what would the procedure be to use my backed up home directory on a fresh install.  Like would I just copy /home to a partition then reinstall off the disk like normal?


Another option I considered is using Acronis True Image and making an image of the whole drive.  Perhaps I would make life easier by simply doing that?

Thanks!

---

### Post by BlueStreak on 2006-10-17
Did a little more research and found this link:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

That should take care of me!

---

### Post by kspringer on 2006-10-17
aisyu has a page that answers that, I think.
Check it out:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

k

---

### Post by podunk on 2006-10-17
Backing up the /home directory is sort of like backing up My Documents in Windows. If your OS crashes then you will need to reinstall and reconfigure quiyte a bit. Video driver for instance, reinstall all your applications, then you can restore your /home directory and have your data.

Once I got a good install I used the command on post #210 of this page:
[http://www.ubuntuforums.org/showthread.php?t=35087&page=21](http://www.ubuntuforums.org/showthread.php?t=35087&page=21)

Unmount your windows and CD drives before starting. :-)

very fast and simple. :-) I'm sure a disk image would work also, never tried it. The above method backed up everything in less than half an hour.

---

### Post by aysiu on 2006-10-17
> **podunk said:**
> Backing up the /home directory is sort of like backing up My Documents in Windows. Right idea, but to be precise, it's like backing up C:\Documents and Settings

---

