---
title: "Setting up common file area"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by jazzgossen on 2007-04-08
I'm trying to set up an area for files accessable by all local users under /home/common, but I'm having trouble getting the permissions right.

/home/common is owned by root and has group "local". I want all members of "local" be able to read and write to all existing and future files under this directory. However, whenever someone adds a new file there, it is owned by that user, and even though that user is part of the "local" group, the file isn't. Furtermore, the file is only writable by its owner.

How can I make it so that files added there are automatically writable by all users of the local group? I could write a cron script that updates the permissions every minute, but there must be a better way, right?

---

### Post by zvacet on 2007-04-08
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Bachstelze on 2007-04-08
When a user creates a file, the file belongs to him/her. As far as I know, you cannot force him/her to give acceess to the file to others, it would just ruin the whole security and privacy model...

Well, you ould just chmod the file as root but I don't know of any other way.

---

### Post by jazzgossen on 2007-04-09
I read about umask, dmask and fmask, that were hinted about in the above link. But to use those masks, do I have to have /home/common on a separate disk partition?

---

### Post by lukew on 2007-04-09
> **jazzgossen said:**
> I'm trying to set up an area for files accessable by all local users under /home/common, but I'm having trouble getting the permissions right.

/home/common is owned by root and has group "local". I want all members of "local" be able to read and write to all existing and future files under this directory. However, whenever someone adds a new file there, it is owned by that user, and even though that user is part of the "local" group, the file isn't. Furtermore, the file is only writable by its owner.

How can I make it so that files added there are automatically writable by all users of the local group? I could write a cron script that updates the permissions every minute, but there must be a better way, right?

Chaneg the file to have a group of local. Do this recursivly for the all containing fiels/dirs. The make the file/folders writable to anyone in the group but remove all permissions from everyone else.

```
sudo chgrp -R local mydir
```
```
sudo chmod 770 -R mydir
```

Luke

---

### Post by lukew on 2007-04-09
Then when you want to change group to local.

newgrp local

---

### Post by jazzgossen on 2007-04-09
> **lukew said:**
> 
```
sudo chgrp -R local mydir
```
```
sudo chmod 770 -R mydir
```


Thanks, but I know about this. What I'm looking for is a way to make the files there owned by the group "local" by default, without having to run chgrp.

---

### Post by lukew on 2007-04-09
> **lukew said:**
> Then when you want to change group to local.

newgrp local

I think the first group in the users group list is the initial group; the one which all files are created under. Can you make it so that the local group is the first group in the list?

---

