---
title: "Cannot log in"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by zumbi77 on 2007-03-27
Hi

I can't log into gnome. Tried to log in to terminal mode, and it seems like the hard disk is full. 
Not sure what happened, but I think there is some kind of backup program running that duplicates my data, filling up my disk.

Tried running sudo aptitude clean, but that only released a little space, so I still can't log in.

What can I do to now?

---

### Post by Kobalt on 2007-03-27
You could start a LiveCD session, mount your hard drive form there and delete the unnecessary files filling you HD... 
Start up your Live session and use these commands in a Terminal to mount your HD
```
sudo -s
mkdir /mnt/tmp
mount /dev/hdax /mnt/tmp
```
Replace *hdax* by your partition label on which /home is, you can find that in your fstab (if you didn't place it on a separate partition it should be on "/") :
```
cat /etc/fstab
```
Then you will be able to access your HD with nautilus, from the path /mnt/tmp. Beware, do not remove files you don't know anything about if it's not in your /home directory.

---

### Post by tagginannie on 2007-03-27
> **zumbi77 said:**
> Hi

I can't log into gnome. Tried to log in to terminal mode, and it seems like the hard disk is full. 
Not sure what happened, but I think there is some kind of backup program running that duplicates my data, filling up my disk.

Tried running sudo aptitude clean, but that only released a little space, so I still can't log in.

What can I do to now?

Reboot and choose rescue mode. **This will give you full root access** so be careful because you can mess up your system if you are not. At the prompt type "rm /var/backup/ df -h" with out the quotes. If you get an error message
saying that it cannot delete than try, " rm -ri /var/backup/*

---

### Post by zumbi77 on 2007-03-27
Trying out the last tip I get the following error message:

cannot lstat '/var/backup/*' : No such file or directory

I'll have to wait to get I home to try out the other advice.

---

### Post by zvacet on 2007-03-27
It is **var/backups**

---

### Post by zumbi77 on 2007-03-28
Hi

I still can\t get this to work.

Tried removing /var/backups/, but that didn't make any difference.

Then I mounted the hard disk using a live cd. I found the backup file that was causing the problems and deleted it. Unfortunately, that didn't solve my problems.

If I use the live cd and mount /dev/hda1, a message pops up saying that the hard disk is 100% full. But if I go to /mnt/tmp/dev/hda1 it only contains about 15 G of data ( the size of the disk is 27 G). So it seems like the file I deleted is somehow stored on my disk, but not on /dev/hda1???

Then I tried deleting some of my music files, but I can't because I don't "have permission to modify the parent folder":confused: 

Any advice will be appreciated.

Resolved: Didn't understand that I had to be root. Typed gksudo nautilus, and then I could delete files. The backup file was in the hidden trash folder. Found it, and deleted it. Voilá.

Thanks for the help

---

