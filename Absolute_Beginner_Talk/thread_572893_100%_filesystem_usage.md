---
title: "100% filesystem usage"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by dmunc on 2007-10-10
Hello all,

I guess the title suggests I'm pretty new to Ubuntu (7.04), but a few days ago I scrapped windows entirely and did the default install on the entire hard disk.

I've been trying to back up the new system to a 320 GB USB hard drive (unsuccessfully) using Simple Backup, et. al. Tried Simple Backup again, but instead of choosing the external hard drive I must have chosen some place on the laptop hard drive to backup to.

My hard disk usage is 100% and I can't boot in at all (using a Live CD now). I can't make any sense of Disk Usage Analyzer as the usage never adds up to the total drive capacity (35 GB).

What/where can I delete? This is obviously quite urgent... :P

Thanks!!
Dan

---

### Post by scrooge_74 on 2007-10-10
check your /home/username/.Trash folder and delete items

also you can start your system without the Live CD and go to a terminal and type sudo apt-get remove to purge downloaded packages you are no using any more.

check in /var/log there you can delete log files taking up space.

---

### Post by defrex on 2007-10-10
Also, try and remember where you put your backup. That's probably the cause of the problem. If you delete that, it may fix it. I'm not familiar with the backup solution you mentioned (and if it allows this), but if you were recursively backing up the backup file you could fill your disk pretty fast.

---

### Post by dmunc on 2007-10-11
Well, I know where I *intended* to place the backup!

It doesn't help that I'm not too familiar with the Ubuntu file system yet... but I KNOW I had about 16 GB of data before I started this backup mess (ironically responsible for crashing my computer!). My hard drive is 35 GB, so I'm guessing the "backup" went as far as it could.

I'm also having various permissions issues. I'll give your suggestions a shot but unfortunately it looks like I might be starting fresh...I'll be more careful next time! Hopefully I can extract some important files beforehand...

Perhaps I'll wait for 7.10... :P

Thanks!
Dan

---

### Post by scrooge_74 on 2007-10-11
Next time with what ever version of Linux you use first partition your drive in at least three sections: the system, a swap file and your /home directory.  That way things are easierto set up. And don't forget to backup  ;)

---

