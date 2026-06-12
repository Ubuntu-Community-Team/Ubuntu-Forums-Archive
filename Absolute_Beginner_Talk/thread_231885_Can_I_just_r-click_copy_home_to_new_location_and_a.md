---
title: "Can I just r-click copy /home to new location and adjust fstab?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-08-07
I was wondering for backup purposes to move /home from hda4 to hda2 root and then edit the fstab.

Is this possible without having to run liveCD or can it be done my way?

If it is possible do I have to state for home in root in fstab?

I ask because if I remeber correctlly when I had it install by defualt  before I don't remeber fstab having a mount point for /home.

Any Help is appreciated.

---

### Post by simonn on 2006-08-07
Yes and no.

Moving it is easy. However, you will have to log out all users that have their /home directory on home and move it using a user which does not have their home directory on /home. In most distros this could be done by root (who's home is /root), however Ubuntu does not have root enabled by default.

So, you would have to either enable root, log everyone out then log in as root or boot from a live cd.

Then:

 - move /home/* to another partition
 - setup fstab to mount the above partition to /home

---

### Post by orb9220 on 2006-08-08
Thanks for the info.

---

### Post by eXisor on 2006-08-08
Hold off before you do this. Just moving it the way the previous poster suggested could mess up all the symbolic links.

Take at a look at [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) to see how to preserve those too.

The line you're particularly interested in is 
```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

---

### Post by simonn on 2006-08-08
> **eXisor said:**
> Just moving it the way the previous poster suggested could mess up all the symbolic links.


No it won't.

If you cp a symlink without the -d flag (or -no-dereference --preserve=link) then the file a symlink points to will be copied, not the symlink itself.

If you mv a symlink, the symlink is moved.

The find line in the article could probably be replaced with a cp -a.

---

### Post by mlind on 2006-08-08
Just drop to runlevel 1 by executing 
```

sudo init 1

```
Do what you need for home partition, and go back to runlevel 2. No need to "enable" root account. 

I would backup my $HOME folder using tar
```

tar cf - . | ( cd /path/to/target; tar xpf -)

```

---

### Post by orb9220 on 2006-08-08
Well Thanks for the info I shall 

"Sacrifice One virgin Microsoft Employee to the fires of Goddess Ubuntu"

---

### Post by eXisor on 2006-08-08
The cp command can fail if there is too much to copy (it has a fixed input buffer size). That's why the article uses find and the piping mechanism.

---

### Post by simonn on 2006-08-08
> **eXisor said:**
> The cp command can fail if there is too much to copy (it has a fixed input buffer size). That's why the article uses find and the piping mechanism.

I have never heard this, do you have a cite?

I cannot see how a fixed input buffer would be a problem.

Personnally, I have copied Gbs of data, including files over 2Gb (or even 3Gb) using cp and never had a problem.

---

### Post by eXisor on 2006-08-08
simonn:

I could've sworn I read it somewhere on these forums, but can't find a link. So until I do... my bad!

---

### Post by steve.horsley on 2006-08-08
It might be a problem with the argument list if you "cp *" on a directory with a huge number of files - it uses shell expansion to build hte file list before calling the cp executable.

---

### Post by eXisor on 2006-08-08
Thanx Steve. I remember seeing a thread that covered exactly that point around here somewhere. Can't for the life of me recollect the subject matter of the thread though.

---

### Post by simonn on 2006-08-10
You learn something new everyday.

steve.horsley, you are correct [http://www.linuxjournal.com/article/6060](http://www.linuxjournal.com/article/6060)

However, it looks as if you can use the following safely:

```

$ cp -a /srcdir/. /destdir

```

I have not done substantial testing, but the shell does not expand the . like it does the *.

Create a script like below:

```

#!/bin/bash
echo "($@)"
echo "($1) ($2) ($3)"

```

Compare the results of 

```

$ [script] . 
$ [script] *

```

---

