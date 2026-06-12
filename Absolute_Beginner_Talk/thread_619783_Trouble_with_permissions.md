---
title: "Trouble with permissions"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-11-21
I have just used gparted to reformat a partiton on my hard drive from ntsf to ext3. I have mounted it in media but now I am having trouble understanding how to change permissions. I want all users to be able to read and write to it.

this is my line in fstab.

```
/dev/sda2 /media/sda2 ext3 defaults 0 2
```

I know that this is basic Ubuntu stuff but for some reason my brain can't digest changing permissions when it comes to a partition.

---

### Post by skyjacker on 2007-11-21
Wouldn't this be handled under "system settings/user administration"??

---

### Post by cwrann on 2007-11-21
I can't find a system settings or a user administration option under administration.  or preferences.

---

### Post by p_quarles on 2007-11-21
Let me make sure I understand correctly: you've gotten the partition to mount automatically, but no one can access it without root privileges?

If that's right, my first question would be whether this is a permissions issue or an ownership issue. Can you run this?:
```
ls -l /media
```
Then, post the line for /media/sda2

---

### Post by geirha on 2007-11-21
I suggest you create a group, let's say you call it *sharing*. Add all users that should have access to /media/sda2 to that group. Then change group ownership of the filesystem with ```
sudo chgrp *sharing* /media/sda2
```
and give the group read and write access ```
sudo chmod g+rws /media/sda2
``` The s in **g+rws** sets the setgid-bit. Any new file and directory created within /media/sda2/ will then inherit the group-ownership of it's parent directory.

---

### Post by cwrann on 2007-11-21
```
drwxr-xr-x  3 root root 4096 2007-11-21 16:33 sda2

```

the line for a partition that I can read and write to is

```
drwxr-xr-x 15 home home 4096 2007-11-19 17:12 sda1
```

thank you for the reply.

---

### Post by p_quarles on 2007-11-21
Cool. This should be easy to solve. If you actually want a different group for this second partition, you can follow geirha's instructions, and then add the users you want to access that partition to the group "sharing."

If you want this new partition to have exactly the same status as /dev/sda1, you can do this:
```
sudo chown home:home /media/sda2
```

---

### Post by cwrann on 2007-11-21
Thank you geirha and p_quarles, I went with p_quarles fix because it seemed like the "cleaner" way to do it. It worked perfect.

I am curious I know that chown changes the ownership of a file. what does the** :** do.  In other words if you could translate that into layman's terms I would appreciate it.

Thanks again to both of you.

---

### Post by geirha on 2007-11-21
Doing "chown foo:bar file" is the same as doing "chown foo file" and "chgrp bar file", you just set both user ownership and group ownership in one command instead of two.

---

### Post by p_quarles on 2007-11-21
> **geirha said:**
> Doing "chown foo:bar file" is the same as doing "chown foo file" and "chgrp bar file", you just set both user ownership and group ownership in one command instead of two.
Exactly. In *nix, each file has both a user owner and group owner. The command I gave was just an easy way of changing both from "root" (which is locked down) to "home" (which is how the other partition was configured). 

Anyway, in your current configuration, only user owners will be able to write files to that directory. If you want to add that ability for other members of the group "home", you can run this:
```
sudo chmod 775 /media/sda2
```

---

