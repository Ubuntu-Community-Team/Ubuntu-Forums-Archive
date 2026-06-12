---
title: "[help] disk format"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-11
Hi,

I'm trying to format a drive in ext3 file system, using gparted tool.

However, I'm always noticing about 1.3 GB used on an 80 GB drive.
Is this normal?  How can I regain this 1.3 GB?

Thanks.

---

### Post by lazyart on 2007-06-11
That 1.5% is probably overhead for the file system.  The only way to have it all is to not format it, but then it's useless that way.

---

### Post by Inxsible on 2007-06-11
EXT3 is a journalling file system. It is probably using that space for it. Don't worry about it. 1.625 % is not that bad anyway :)

---

### Post by stchman on 2007-06-11
> **pcandpc said:**
> Hi,

I'm trying to format a drive in ext3 file system, using gparted tool.

However, I'm always noticing about 1.3 GB used on an 80 GB drive.
Is this normal?  How can I regain this 1.3 GB?

Thanks.

The EXT3 file system has a 5% overhead.  It should be 4GB not 1.3.

---

### Post by pcandpc on 2007-06-11
Hi,

On the other hand, if I choose reiserfs, then the used space shrinks
to 34.49 MB.

By the way, when I'm formatting the drive in ext3, I'm getting an error
message that says unable to mount the volume with the following details:

mount_point cannot contain the following characters: newline,
G_DIR_SEPARATOR (usually /)

If I just ok this message window, the format in ext3 gets completed,
but there's always this 1.3 GB used out of 80 GB.

Thanks.

---

### Post by Inxsible on 2007-06-11
> **pcandpc said:**
> Hi,

On the other hand, if I choose reiserfs, then the used space shrinks
to 34.49 MB.

By the way, when I'm formatting the drive in ext3, I'm getting an error
message that says unable to mount the volume with the following details:

mount_point cannot contain the following characters: newline,
G_DIR_SEPARATOR (usually /)

If I just ok this message window, the format in ext3 gets completed,
but there's always this 1.3 GB used out of 80 GB.

Thanks.
EXT3 stores all the data in the journal, that needs to be backed up in case of a crash. Reiserf, AFAIK, only stores the meta-data. Thats why you see it taking a lot less space.

For your error: what is the mount point that you are selecting ?

---

### Post by pcandpc on 2007-06-12
Hi,

When formatting, I can only choose partition and filesystem types.

There's no option to choose a mount point; perhaps, this is the problem?

So then, how does the reiserfs compare to ext3?  I mean is it better
and more efficient than ext3?  At least, reiserfs wastes less space, right?

Thanks.

---

