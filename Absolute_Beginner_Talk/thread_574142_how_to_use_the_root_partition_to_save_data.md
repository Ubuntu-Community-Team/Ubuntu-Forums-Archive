---
title: "how to use the root partition to save data?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by taisao on 2007-10-12
Hi, 

I have a partition for "/" and another for "/home". Now I want to save my userdata in the "/" partition too. Because the free space on "/home" partition is getting smaller by day.

Do I just need to create a folder in the "/" partiton and change the permission as my "/home/username" (which is drwxr-xr-x 88 username username)? 
And what is the number 88 exactly? (containing files?)



```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              65G  5.4G   56G   9% /
/dev/sda6             117G   87G   25G  78% /home
```

---

### Post by Bliepo32 on 2007-10-12
Well, you cannot really use the root partition to save data from the /home partition. You can move the from your /home to /, but you cannot make / your /home partition. You could resize the disk though, without losing any data.

Alternatively, you could make a /home2 folder, and the move the files you want to move to it. The code for it would be this.

```

cd /
sudo md home2
sudo mv /home/[yourusername]/Desktop/[filenameyouwanttomove] /home2

```

---

### Post by phr0ze on 2007-10-12
I'd try the resize option first. 

Shrink your root, then after it's done, make sure everything is ok, then grow your home folder.  If you are nervous about growing your home folder, create a new partition and set it's mount point into your home folder.

Example,

/Home/user/moredata could actually point to another partition, but the system wont care.

---

### Post by taisao on 2007-10-12
Uhm, I think u guys didn't understand me. Maybe because I didn't explain it to well. Anyway I just want to create a folder in the root partition which a user 'usernameX' can use. This is what I have done:

```
sudo mkdir /home2_usernameX
sudo chown -R usernameX:usernameX /home2_usernameX 
```

It seems to works, I just move 4GBs from sda6 to sda1 partition.

---

