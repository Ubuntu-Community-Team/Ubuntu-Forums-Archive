---
title: "advice for making systen backup"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by petegreenhorn on 2008-03-31
Hi i'm following (or should i say trying to follow) this post for backing up my sytem [http://ubuntuforums.org/showthread.php?p=175981#post175981](http://ubuntuforums.org/showthread.php?p=175981#post175981). 
what i need to know is ? i want to make the backup to my external HD ( /media/disk ) do i need to exclude it from the backup code : i.e   --exclude=/media/disk   or should it be something else 
also the restore code : should be entered whilst in the ( external HD directory ) right :confused:

---

### Post by abhiroopb on 2008-03-31
> 
Now come the directories we want to exclude. We don't want to backup everything since some dirs aren't very useful to include. Also make sure you don't include the file itself, or else you'll get weird results.
You might also not want to include the /mnt folder if you have other partitions mounted there or you'll end up backing those up too. Also make sure you don't have anything mounted in /media (i.e. don't have any cd's or removable media mounted). Either that or exclude /media.


so yes I guess best would be to do:
--exclude=/media

Yes you will have to be in the SAME folder as the zipped file to restore the files.

I personally like using partimage to backup. It creates an identical copy of the current system. Its effective and restore is not a problem, but it can be slow (upto 9-10hours for 50gb of data).

more information: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by petegreenhorn on 2008-03-31
thanks abhiroopb, second time today

---

### Post by mister_pink on 2008-03-31
Try installing simple backup from the repos. It'll automate the task and is much more user friendly than that!

---

### Post by abhiroopb on 2008-03-31
glad to have helped!

---

### Post by TheWizzard on 2008-03-31
> **petegreenhorn said:**
> Hi i'm following (or should i say trying to follow) this post for backing up my sytem [http://ubuntuforums.org/showthread.php?p=175981#post175981](http://ubuntuforums.org/showthread.php?p=175981#post175981). 
what i need to know is ? i want to make the backup to my external HD ( /media/disk ) do i need to exclude it from the backup code : i.e   --exclude=/media/disk   or should it be something else 
also the restore code : should be entered whilst in the ( external HD directory ) right :confused:

I'm not a big fan of this backup method. 
the only things you really need to backup are /home and /etc. 

i advice you to use a method with rotating snapshots - like timemachine in osx. 
you can try this:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

or TimeVault:
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by dje on 2008-04-14
Take a look at my new project linbaku, it creates complete backups of your ubuntu installation and should cater for your needs. For more information see the blue linbaku link in my signature.

hope that helps,
dje

---

### Post by abhiroopb on 2008-04-14
Many many thanks. I use partimage, so was wondering if this does essentially the same thing: i.e. backup EVERYTHING as an image, so that if I ever want to I can simply erase my current install and just restore that image. However, partimage is slow and I need to use a liveCD to use it, so if this does it straight from the desktop then its for me, is this so?

---

### Post by hyper_ch on 2008-04-14
> **TheWizzard said:**
> the only things you really need to backup are /home and /etc. 

and /etc and /var/www and /var/lib/mysql .....

---

### Post by TheWizzard on 2008-04-14
> **hyper_ch said:**
> and /etc and /var/www and /var/lib/mysql .....

for a desktop pc /home and /etc is sufficient. 

for packages you can use:
$ dpkg --get-selections | grep -v deinstall > installed-software.log

and restore with:
# dpkg --set-selections < /backup/installed-software.log

---

