---
title: "CLI to partition to edit a file [Resolved]"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by ifthengoto on 2007-05-18
Beginner CLI question.

If I am at a terminal and I want to edit my menu.lst file which is at partition SDB4 on my hard drive how do I do it?

Normally the file is at /dev/sdb4 but then how do I get to gedit /boot/grub/menu.lst

sdb4 is a partition and not a directory?

(hope that makes sense).

---

### Post by n0dl on 2007-05-18
Since you are a beginner at CLI  you should learn how to use VI or EMACS but using nano is ok for now. To edit a file simply type 
```
nano /path/to/file
``` 
where "/path/to/file" is the absolute pathname to the file. After you are done editing the file simply press ctrl x to quit and save

---

### Post by NikoC on 2007-05-18
Isn't the device mounted in /media?
Via /media/sda1 I can access my Windows drive (and files) which is on separated partition.

---

### Post by freebird54 on 2007-05-18
A couple of ways to do it from the CLI.  One is to 'go' there, then edit.  The other (as mentioned before) is to specify the file completely.

Method 1 example
```

cd /dev/sdb4/boot/grub
gedit menu.lst
```

OR (variation as desired)

```
cd /dev/sdb4
gedit boot/grub/menu.lst
```

Method 2 example

```
gedit /dev/sdb4/boot/grub/menu.lst
```

There's a couple of choices for you!  BTW - this means you are changing a file 'behind the back' of the OS it belongs to.  So - you don't need sudo to acccess it this way.  If you were booted into the system in question, you would need 

```
gksudo gedit *<whatever_path_and_file>*
```

to access a system file...

Hope this helps...
s

---

### Post by FuturePast on 2007-05-18
> **freebird54 said:**
> 
There's a couple of choices for you!  BTW - this means you are changing a file 'behind the back' of the OS it belongs to.  So - you don't need sudo to acccess it this way.  If you were booted into the system in question, you would need

Umm, which system lets you do this?

To answer the OP: the partition contains a filesystem.
You need to mount the filesystem before you can access any of the files that reside within that filesystem.
e.g. $ mount /dev/sdb4 /mnt/random_dir

---

### Post by freebird54 on 2007-05-18
Anytime you have multiple OS's on your computer, there is no default mechanism for OS#1 to respect the permissions of OS#2 - if you just mount the partition accessible by the user of OS#1.  For example, I run Edgy and Feisty on here - and if I mount the Feisty drive from Edgy I can access any part of Feisty from the default user of Edgy as showin the previous post.  It appears that is what is happening with the original poster as well.  Of course, if it isn't it won't work and we'll hear back! :)

BTW - this is why physical security is important to those who want their files inaccessible - anyone with a Live CD can get into the filesystem(s) available on the computer.  It is also why we can fix things that go wrong by the same means!  IF you want your files pretty secure - keep them encrypted!

---

### Post by FuturePast on 2007-05-18
Oh, you mean this:
```
~$ mount
...
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
...
$

```

/dev/sda1 is very, very different to /media/sda1 .

---

### Post by aysiu on 2007-05-18
Just paste these commands into the terminal: ```
sudo umount /dev/sdb4
sudo mkdir /recovery
sudo mount /dev/sdb4 /recovery
gksudo gedit /recovery/boot/grub/menu.lst
```

---

### Post by ifthengoto on 2007-05-18
> **aysiu said:**
> Just paste these commands into the terminal: ```
sudo umount /dev/sdb4
sudo mkdir /recovery
sudo mount /dev/sdb4 /recovery
gksudo gedit /recovery/boot/grub/menu.lst
```

Thanks to all - the above worked. 

I was actually trying this because I had installed a second version (xubuntu) of Ubuntu on my USB drive so I could have an experimental zone to test stuff (and maybe learn). Unfortunately I cannot get it to boot.

---

### Post by freebird54 on 2007-05-18
Oops!  Posting faster than I was reading... :oops:

Yes - gotta mount it first - (I already had) - THEN the rest applies... :)

---

