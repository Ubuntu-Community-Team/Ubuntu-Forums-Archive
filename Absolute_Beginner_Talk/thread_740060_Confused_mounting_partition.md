---
title: "Confused mounting partition"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dragon-architect on 2008-03-30
Okay, I've been playing with the command line recently, so I've wanted to figure out how to mount a data partition to a folder on my desktop. I already have the directory made and I have a basic grasp of the commands, but when I type

sudo mount /dev/sda1 /home/calyodelphi/Desktop/data

and then access the folder, there are little padlock icons on all the folders and files. Can anyone tell me what I've done wrong? I'd really love to be able to mount this partition with read/write permissions since I'm the only user of my computer and this partition has several gigs of data that I use daily.

Other information that could help is that this drive's ID is sda1 (had to install gparted to figure that out x_x ) and the filesystem is fat32. I dunno how much relevance this will have, but I figured that giving information helps.

---

### Post by cotcot on 2008-03-30
You have no user permission on the mounted file. 
If you access the partition with ```
gksudo nautilus
``` you will not see the padlocks.

---

### Post by dragon-architect on 2008-03-30
I was kinda hoping I'd have to avoid having to enter my admin password by mounting via the command line. Perhaps if I mounted to a different directory that wasn't in my home folder? Would that make it easier to access without the padlocks? Maybe somewhere like /media/disk or /media/data or something like that that I'm somewhat familiar with?

---

### Post by dsauxier on 2008-03-30
Give yourself permissions on everything (do this with the partition mounted)
770 means read/wrtie/execute for owner and group and no permissions for anyone else.
the "-R" means it will recurse through all subdirectories.

```

sudo chmod -R 770 /home/calyodelphi/Desktop/data
sudo chown -R calyodelphi:calyodelphi /home/calyodelphi/Desktop/data

```

---

### Post by dragon-architect on 2008-03-30
I encountered an error. When I typed in the chown command, I got a bunch of "Operation not permitted" when it went through all the files. I can't even copy&paste what I typed because the terminal buffer overflowed and cut off the code entries.

EDIT: and when I opened the directory, I got a popup saying "Folder contents could not be displayed. You do not have permissions necessary to view the contents of 'data'."

---

### Post by dsauxier on 2008-03-30
> **dragon-architect said:**
> I encountered an error. When I typed in the chown command, I got a bunch of "Operation not permitted" when it went through all the files. I can't even copy&paste what I typed because the terminal buffer overflowed and cut off the code entries.

EDIT: and when I opened the directory, I got a popup saying "Folder contents could not be displayed. You do not have permissions necessary to view the contents of 'data'."

Of course ... sorry, I forgot that fat32 works different than ext3 for permissions/ownership.
You can mount the drive such that it is readable by all : 

First, unmount it 
```

sudo umount /home/calyodelphi/Desktop/data

```

To make this easier, add a line to /etc/fstab (this will also make it automount when you boot)
I'm assuming that your uid is 1000
You can verify by opening up System->Administration->Users and Groups
Double-click your userid and click the "Advanced" tab.
There's a grayed-out "User ID" field, that's your UID
```

/dev/sda1      /home/calyodelphi/Desktop/data      vfat     rw,auto,umask=000,uid=1000,gid=1000 0 0

```

Now you can simply mount it : 
```

sudo mount /home/calyodelphi/Desktop/data

```

---

### Post by dragon-architect on 2008-03-30
and with that entry in fstab, it'll mount with read/write permissions no matter where I mount it?

EDIT: Well, that is if I edit the entry to reflect the mount directory of course. ^^; Forgot to mention that.

---

### Post by dsauxier on 2008-03-30
> **dragon-architect said:**
> and with that entry in fstab, it'll mount with read/write permissions no matter where I mount it?

EDIT: Well, that is if I edit the entry to reflect the mount directory of course. ^^; Forgot to mention that.

Yes, that's how it should work.

---

### Post by dragon-architect on 2008-03-30
Subliiime! 8) Thanks a lot for the help.

---

