---
title: "Backing up"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-21
I know, i know. This is the ultimate uber-newbie question. But i have never backed a single thing up in all my life. Always, to shamed to ask. But not anymore 

I need to do a fresh install in order to creat a dual boot. Besides i have heard some say it is better to do a clean and fresh Breezy install opposed to upgrading.

Whether it is or not. Because i want to dual boot i need to do a fresh install anyhow and this gives me the change to also ask how to back-up. I want to bring and carry over all my bookmark settings for epiphany and firefox and opera. I also want to save my emails and addresses and other documents. 

How do i do that please?
I found a great link to show me how to back up, which i'm doing now:
[http://www.ubuntuforums.org/showthread.php?t=35087&highlight=back-up](http://www.ubuntuforums.org/showthread.php?t=35087&highlight=back-up)
However, i think i'm backingup my whole system with tar xvpzf backup.tgz ....
Which i don't need because i'm doing a fresh install anyways. 
In this case all i need to do is backup /home/username or /home?

Again

thanking you way out in advance,

Yours truly,

--
sophtpaw

---

### Post by SilentCacophony on 2005-09-21
Hello. I don't think just backing up your home directory will suffice, as I find that some settings like personal bookmarks in firefox are stored under /etc/mozilla-firefox/profiles/.

Many programs will let you export information for backup and migration purposes. For example, Firefox allows you to export your bookmarks by choosing *Bookmarks* > *Manage Bookmarks* then choosing *File* > *Export*, then choosing a name and location to save them.

If you do a full backup, you'll still need to know where to retrieve the files from, so exporting/importing can often be easier. Anyway, your home directory and /etc contain much of your setup, and other things like themes are often stored in usr/share.

---

### Post by davmac on 2005-09-21
Personally I keep a full backup on DVD+RW but I only update this every month or so. If push comes to shove I can rebuild the system from scratch without too much effort.

The only part of the system I couldn't easily rebuild is /home so I use rsync to do a frequent backup of this. If my USB keyring is plugged in the script will also rsync with this too. If you want the script I use to do this just shout.

Regards,

Dave Mac

---

### Post by mlomker on 2005-09-21
> In this case all i need to do is backup /home/username or /home?


Look at my comments in [this thread.](http://www.ubuntuforums.org/showthread.php?t=67407&highlight=tar+xvvf)

---

