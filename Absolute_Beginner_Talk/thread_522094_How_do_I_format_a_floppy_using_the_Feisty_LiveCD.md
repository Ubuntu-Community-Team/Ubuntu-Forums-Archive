---
title: "How do I format a floppy using the Feisty LiveCD?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-08-10
I need to format a floppy from the Feisty LiveCD.

There is no Application>System Tools>Floppy Formatter.  I checked under System>Preferences>Main Menu.

The floppy was originally formatted under XP. There are no files on the disk.  I cannot mount the floppy.. When I try to mount the floppy, I receive an "unable to mount" error.

There is no right-context menu entry for Format. There probably is when the floppy is mounted, but I cannot mount the floppy.

So, does anyone know how I can go about formatting a floppy with the Feisty LIveCD?

Thanks..

---

### Post by hamburglar6 on 2007-08-10
in a terminal window, type
```
cat /etc/fstab
```
and check for a line relevant to your floppy drive.  it should be something like

/dev/fd0        /media/floppy     blah blah

assuming this is the case, and that you want to format your partition as ext3 you can do the following in a terminal:
```
mount /dev/fd0
mkfs -t ext3 /dev/fd0
```

and that should do it.

---

### Post by MindRiot on 2007-08-10
Remember, I'm using the LiveCD.

This is the contents of the fstab for the LiveCD

> ]unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hdb4 swap swap defaults 0 0

It simply will not work to add the necessary line.

---

### Post by philinux on 2007-08-10
Synaptic comes loaded with fdutils. this is not gui though. It's a set of command line utilities. One of which happens to be fdformat.

On an installed system there is a gui in the shape of Kfloppy installed via synaptic its nor preloaded

---

### Post by hamburglar6 on 2007-08-10
i'm not completely sure you even need to mount the floppy to format it.  just try the bit about mkfs and see if that works.

---

### Post by MindRiot on 2007-08-10
Thanks for the replies.

**When I enter:**

```
mkfs -t ext3 /dev/fd0
```

**This is returned**

> ubuntu@ubuntu:~$ mkfs -t ext3 /dev/fd0
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=1572864
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done                            

Filesystem too small for a journal
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 32 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

**Then, when I enter:**

```
mount /dev/fd0
```

**I get this error message:**

> mount: wrong fs type. bad option, bad superblock on /dev/fd0, missing code page or other error  In some cases, useful info is found in syslog - try dmess | tail or so.

Why it won't mount is beyond me.

---

### Post by philinux on 2007-08-10
I know I'm not on the live cd but when I look in places computer it shows my floppy drive. If I right click I then get option to mount.

Have you tried fdformat from the terminal

---

### Post by hamburglar6 on 2007-08-10
the reason it won't mount is you don't have a /media/floppy0 folder.  normally all you would have to do to fix this is a simple

```
sudo mkdir /media/floppy0
```

if you absolutely need to do this with the livecd running however, i'm not sure there is any way to do this.  if there are any empty folders anywhere on the livecd's filesystem you could probably do a 
```
mount /dev/fd0 /path-to-empty-folder
```

---

### Post by hamburglar6 on 2007-08-10
oops.... i didn't read your post correctly.  change the previous mkfs command to read:
```
mkfs -t ext3 /dev/fd0 1440
```

also if that doesnt immediately solve your problem, modify your mount command to read:
```
mount /dev/fd0 /media/floppy0 ext3 rw,user
```

---

### Post by hamburglar6 on 2007-08-10
ugh ok brain fart again.  if you modify your fstab change the line about the floppy to read what i said in the mount command in the previous post.  if you cant use this mount command:
```
mount -t ext3 /dev/fd0 /media/floppy0
```


...three times a charm.

---

### Post by MindRiot on 2007-08-10
> **philinux said:**
> Have you tried fdformat from the terminal

O.K. Phil, I ran fdformat, and it definitely formatted the floppy disk.  That's great.

But, when I try to mount the floppy from the file browser I get:

> mount: you must specify the filesystem type

If I then try to mount the floppy from the terminal, by typing:

```
mount /dev/fd0
```

I got this error message:

> mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab

So, I added to fstab the following line:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and then, once again, I entered:

```
mount /dev/fd0
```

And I got this error message:

> mount: mount point /media/floppy0 does not exist

---

### Post by mattmole on 2007-08-10
Have you created the directory?

sudo mkdir /media/floppy0

mattmole

---

### Post by hamburglar6 on 2007-08-10
so then what i said a few posts back is what the problem is.  you don't have a /media/floppy0 folder.  check that post out and reply back if you have any more problems.

---

### Post by MindRiot on 2007-08-10
> **mattmole said:**
> Have you created the directory?

sudo mkdir /media/floppy0



Yes, I typed

```
sudo mkdir /media/floppy0
```

and then I followed hamburglar6's advice::

> **hamburglar6 said:**
> the reason it won't mount is you don't have a /media/floppy0 folder.  normally all you would have to do to fix this is a simple

```
sudo mkdir /media/floppy0
```

if you absolutely need to do this with the livecd running however, i'm not sure there is any way to do this.  if there are any empty folders anywhere on the livecd's filesystem you could probably do a 
```
mount /dev/fd0 /path-to-empty-folder
```

When I type:

```
sudo mount /dev/fd0 /media/floppy0
```

I get:

> mount: you must specify the filesystem type

Again, thanks for the help.

---

### Post by hamburglar6 on 2007-08-10
when doing the mount command you need to specify the type with the -t option like i said a few posts ago:
```
mount -t ext3 /dev/fd0 /media/floppy0
```

---

### Post by MindRiot on 2007-08-10
> **hamburglar6 said:**
> when doing the mount command you need to specify the type with the -t option like i said a few posts ago:
```
mount -t ext3 /dev/fd0 /media/floppy0
```


Thanks for taking time to help, I do appreciate it.

I tried entering:

```
sudo mount -t ext3 /dev/fd0 /media/floppy0
```

And this error message came back:

> mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'd look into the syslog, but I don't know which directory its located.  Furthermore, I haven't a clue what

> dmesg | tail  or so

is suppose to mean.

---

### Post by philinux on 2007-08-10
Now you've got the floppy0 directory does the floppy show up when you look at Places>Computer?

---

### Post by hamburglar6 on 2007-08-10
i think it said previously when you formatted the disk that it was too small to create a journal- if it created an ext3 fs with no journal that is equivalent to an ext2 fs.  try using 
```
sudo mount -t ext2 /dev/fd0 /media/floppy0
```

and see what happens.

---

### Post by MindRiot on 2007-08-10
> **philinux said:**
> Now you've got the floppy0 directory does the floppy show up when you look at Places>Computer?

No, it doesn't show up, (There is a floppy icon, and always has been, but not a floppy0 icon) But I suspect that is because I have added the needed line to fstab.  The folder /media/floppy0 does exit, as I can navigate to it in the computer browser or change directory to it in the terminal.


> **hamburglar6 said:**
> i think it said previously when you formatted the disk that it was too small to create a journal- if it created an ext3 fs with no journal that is equivalent to an ext2 fs.  try using 
```
sudo mount -t ext2 /dev/fd0 /media/floppy0
```

and see what happens.

Unfortunately, I get the same error message:

> ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/fd0 /media/floppy0
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by hamburglar6 on 2007-08-10
well thats upsetting...i have to say i have no idea why that's happening.  try starting again from the mkfs step, but this time use ext2 instead of ext3.  there isn't any reason to use ext3 over ext2 in this instance, so you're not losing anything by doing that. let us know how it goes.

---

### Post by philinux on 2007-08-10
What shows when you right click on the Floppy icon?

---

### Post by MindRiot on 2007-08-10
> **hamburglar6 said:**
> well thats upsetting...i have to say i have no idea why that's happening.  try starting again from the mkfs step, but this time use ext2 instead of ext3.  there isn't any reason to use ext3 over ext2 in this instance, so you're not losing anything by doing that. let us know how it goes.

Alright!  That did the trick.  Excellent! Thanks for the help everyone.

So, as you said, I just needed to change the "ext3" in the "mkfs" command to "ext2."

The solution looks simple to me now, but I'm pretty dense.

---

### Post by hamburglar6 on 2007-08-10
glad to hear it worked.  just don't forget to unmount the floppy with
```
umount /media/floppy0
```
or else your files might get corrupted.

Cheers!

---

