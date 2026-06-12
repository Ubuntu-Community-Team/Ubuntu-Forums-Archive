---
title: "[SOLVED] Delete Files using Ubuntu Live CD?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by razeshkale on 2007-06-21
Hi,
I m wondering if you can Delete files on Ubuntu Root using Ubuntu live CD?

Basically i was trying to back up Ubuntu and Did mistake i backed up  on same partition and Now due to HDD room problem i cant log into Ubuntu machine that pops up error message about space on HDD?

so simply i want to delete that backup file and restart using Ubuntu machine?
So if anyone has any idea please let me know?

Cheers

---

### Post by vanadium on 2007-06-21
Did you try?

---

### Post by atria on 2007-06-21
Yes you can. Mount your old ubuntu installation by using this command in the terminal:

```

sudo mkdir /media/ubunturoot
sudo mount -o umask=000 /dev/sdx /media/ubunturoot
```
where sdx is your ubuntu partition. For example /dev/sda1

Just browse to /media/ubunturoot after that. You should see your files there.

[edit]vanadium: instead of posting simple sentences with only three words that make no sense, why not try to post something more constructive?[/edit]

---

### Post by razeshkale on 2007-06-21
Yes i can see the partition but Move to Trash option is disable, ?
File has Read And Write permissions?
so Del key doesnt work?

---

### Post by atria on 2007-06-21
Hmm, the command that i gave you should mount the partition in read/write mode. Does deleting with right click > delete work?

If not try this:
```
gksudo nautilus
```
and browse to that directory again.

Anyway do not use the gksudo command on a live distribution unless you know what you're doing. Screwing up your temporary livecd os is fine, but not your working os, heh.

---

### Post by razeshkale on 2007-06-21
Yes i did try that,doesnt work?
you can find some screen shots on my other post " disk full error"

thanks agian

---

### Post by razeshkale on 2007-06-21
This error i get on login??
Help me

---

### Post by st0nes on 2007-06-21
Are you able to log in if you boot in safe mode?

---

### Post by razeshkale on 2007-06-21
Yes I fixed it!

Mounted Root partition 
and 
Sudo rm /media/mounted image/file name

that remove my backup file which was 12 GB and not i m on my Favorite Ubuntu again
Happy For that
and Thanks for all your help guys! great help

---

### Post by razeshkale on 2007-06-21
> **razeshkale said:**
> Yes I fixed it!

Mounted Root partition 
and 
Sudo rm /media/mounted image/file name

that remove my backup file which was 12 GB and not i m on my Favorite Ubuntu again
Happy For that
and Thanks for all your help guys! great help

issue has been resolved

---

