---
title: "Ubuntu 8.04 booting from USB using persistent mode for saving changes"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by wilsonB on 2008-04-01
Hia all,

I easily got Ubuntu 8.04 to boot up using a 1GB usb. (750mb fat32 partition) Boots fine into live CD mode.
The remainder space formatted ext2 -rw named casper.

At boot, I type persistent and it seems to go.

But then it barks and says 
ext2-fs error (device sda2): ext2_get_inode: unable to read inode bolock - inode=93, block=19
Buffer I/O error on device sda2, logical block 0
lost page write due to I/O error on sda2
It says this for many blocks 

I've been banging my head for a while with this and hope someone could shed some light. 
Did they fix Persistent mode in 8.04?

I even (after standards didn't work) edited the init file in the compressed initrd.gz  to reflect persistent as per;
[http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/](http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/)

Please let me know what file log to post if that helps trouble shooting. 

Thanks so much

---

### Post by ogredeschnique on 2008-07-04
So... 
Have you figured this out? I'm interested in doing the same thing you're talking about, I think. I'm super new to linux.
THanks for any info.:)

(As far as me not searching for it immediately, I'm sure I could find something and probably will have this rockin' pretty quick. I guess I just wanted to participate here. Maybe I'll find something and bring it.)

---

