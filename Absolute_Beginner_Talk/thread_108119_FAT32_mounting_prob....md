---
title: "FAT32 mounting prob..."
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by mozz on 2005-12-25
Hey,

if I mount a fat32 partition, directory names which where all uppercase under windows (e.g. "ARCHIVE") are in linux displayed as "archive" (all lowercase)

Thats quite annoying when I want to sync two fat partitions with rsync, because it interprets this mismatch as a change and therefor sends the whole directory content again :-/

Thanks for any help

---

### Post by Mustard on 2005-12-25
try adding this option below to the mount options (those commands after the -o ) you are entering.

```
check=r
or 
check=n

#These are shorthand for check=relaxed and check=normal which seem to be related to the problem you are having
```

I'd mention that I have never used these and that I just read the mount manual to see what might help.

Type this command below if you would like to read the mount manual yourself.  Hit 'q' to exit the manual when you are finished.

```
man mount
```

---

### Post by aysiu on 2005-12-25
Is there an iocharset=utf8 in your /etc/fstab line?

---

### Post by mozz on 2005-12-26
Hey...sorry for the late answer

Yes, actually there is the iocharset option set (aswell as the codepage)

and the check option didn't help :???:  damn.

I just did a little search in some news groups, and it seems, that this is an problem with the fat drivers? whatever. thanks for your help anyway!

---

### Post by bscbrit on 2005-12-26
Does that mean that you have solved your problem, or you have decided that you are going to live with the problem?  In fact, I am not aware of any problems mounting the FAT32 filesystem.

Can you please give me a link to the information regarding the iffy FAT32 drivers - I may have missed it?

---

