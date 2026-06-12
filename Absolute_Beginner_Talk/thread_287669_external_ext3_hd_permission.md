---
title: "external ext3 hd permission"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tnadenichek on 2006-10-29
hi.

so, i've got a really lovely drive enclosure and a 150gb drive in it. i used gparted to wipe it and reformat it in into 3 logical partitions (a 100gb ext3 and 2 25gb ext2, just for kicks) inside a big extended one. then i ran e2fsck (-f -p) to make sure that there weren't any badblocks.

so, supposedly i should be good to go, right?

the problems arise when i try to use the disk for storing information. specifically only root is permitted to write to the disk (in any of the partitions). convieniently, i have thus far been unable to glean from searches how to change the permissions.

i understand that the default permission for a new ext2/3 partition is root r/w only. 

i've seen two links to [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) which is supposed to walk you through mounting a partion with r/w permission but it doesn't explain it at all and i don't want to set up another place that linux is going to keep files ("/storage"), completely separate from where it is already keeping them. 

i think i'm probably confused on a couple levels, but i've been unable to figure out where my thinking is messing me up.

"a little knowledge is a dangerous thing"

any helpful links or reference suggestions of any kind would be appreciated.

---

### Post by taurus on 2006-10-29
Open a terminal, Applications -> Accessories -> Terminal, and change the permissions for /storage as

```
sudo chmod 777 /storage
```

---

### Post by tnadenichek on 2006-10-29
ok. that worked. much appreciated. 

can you tell me why?

---

### Post by aysiu on 2006-10-29
*chmod* changes permissions (read/write/execute).
*chown* changes ownership (root, user, another user).

---

### Post by taurus on 2006-10-29
> **tnadenichek said:**
> ok. that worked. much appreciated. 

can you tell me why?
"chmod 777 /storage" means you make /storage read, write, and executable for everybody on your system.  That's why you can read, write, and execute anything in /storage.  For more info, you can read the manpage for chmod.

```
man chmod
```

---

### Post by tnadenichek on 2006-10-29
ok. that makes sense. so 777 is allowing write to owner, group, and others to all filesystems mounted to /storage.

why did we need to change ownership if everyone could modify it?

thanks again, everybody.

---

### Post by anaconda on 2006-10-29
hmm..
I prefer this way of using chmod:
sudo chmod a+r /storage
sudo chmod a+rwx /storage
I think this is more readable than 777
"a" comes from all and "r" comes from "read", so a+r is give read rights to all..
and similarly a+rwx means give all users read write and execute rights, which is the same than 777

---

### Post by tnadenichek on 2006-10-29
oops. so when i said that it worked, that's not exactly what i meant. i guess i should have mentioned (though i didn't think it was relevant at the time) that i'd actually been working with a (newly) blank internal hard drive as well as a freshly formatted external one. i followed the instructions from the psychocats too literally and didn't really pay attention to the drive designations. 

now i've got /dev/hda5 pointed to /storage and /dev/sda5 still isn't mounted anywhere i can figure out.

(i only realized this after copying a bunch of files to the internal that i thought were going to the external)

back to basics- is there an existing howto on finding where a device mounts to and changing it? 

you were all really helpful with explaining how to change permissions on filesystems within a mount point - i was totally lost even with two o'reilly books and the whole internet in front of me.

---

