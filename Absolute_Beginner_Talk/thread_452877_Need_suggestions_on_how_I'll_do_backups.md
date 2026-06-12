---
title: "Need suggestions on how I'll do backups"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-05-23
As soon as I get the issues with my external drives figured out, I want to start running backups.  I can probably figure out some simple scripts if someone will point me in the right direction or tell me how they work, but if there is a simple utility that runs in gnome, all the better.

I'm using 7.04 Ubuntu by the way...

All I'll be backing up are things like documents, email, recent photos, and that sort of thing.  I can figure out how to get to all the folders I need to back up, I just need to find out how to automate it.

Thanks for any help...

Eric

---

### Post by Hobo Joe on 2007-05-23
I would recommend doing it manually. As far as email goes, you don't need to back up, it's already on a server somewhere.
So just put all your folders for pictures, documents, etc. on a different partition, then whenever you save a file, save it to those folders. To make it easier you could even put shortcuts the backup folders in their old spots, so you don't have to navigate to the separate partition everytime you want to save something.

---

### Post by ruy_lopez on 2007-05-23
This script will backup your home folder, preserving the permissions:

```
#!/bin/sh

cd "path/to/backup/drive"

tar -cf - -C /home yourhomefolder | tar -xvpf -

```

It's pretty rudimentary, there are better ways of doing backups, incrementally.

this script will only backup files that have changed:

```
#!/bin/sh

rsync -av --delete-after  /home/yourhomefolder  /media/yourbackupdrive/
```

--delete-after makes sure that if you move a file from one directory to another, it doesn't delete the old version until it has successfully backed up the newer one.

See man rsync, for more options. Although it is technically a remote backup utility, rsync can be used locally.

Like the above post says, its better to run these manually, like before you do something you might need to recover from.

---

### Post by Iokua on 2007-05-23
Install sbackup from the repositories. It does full and incremental automated backups.

---

