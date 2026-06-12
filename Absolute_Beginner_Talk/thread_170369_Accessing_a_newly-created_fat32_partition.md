---
title: "Accessing a newly-created fat32 partition?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by æþeling on 2006-05-04
I just created a fat32 partition in qtparted at /dev/hda3. How do I copy stuff on it? I can't find it in the file browser (nautilus).

---

### Post by jorn on 2006-05-04
Try this link:
[http://makuchaku.info/amnesty/#windows](http://makuchaku.info/amnesty/#windows)
If you can't work it out, ask again.

---

### Post by tonyr on 2006-05-04
There must be a file system created on the partition.  I'm not sure
whether **qtparted** does that or not.   If there is a file system, you need 
to **mount** it.  In  a terminal, make a directory in **/media** for that 
partition, then mount it:
```

sudo mkdir /media/hda3
sudo mount -t vfat -o defaults,rw,umask=0000 /dev/hda3 /media/hda3

```

If there is no file system, the **mount** will fail, and you will need to
create one.  I think this should do it, but I've never tried it:
```

sudo mkdosfs -F 32 /dev/hda3

```

Read the man pages for **mount** and **mkdosfs**.

To have the partition mounted at every boot, add an entry to
**/etc/fstab**.  Look at that file and read the **fstab** man page.

If all that works, the partition shows up like any other filesystem, and
you can copy files with whatever tools you are familiar with (cp, tar, mv
drag-and-drop, etc etc etc...)

EDIT:  jorn's post showed up while I was writing this. The link he indicated
looks pretty darn good, a lot more complete than my explanation.

EDIT2:  It looks like **qtparted** has a **Format** operation for creating
the file system.  Did you do that?

---

### Post by æþeling on 2006-05-04
[QUOTE=jorn]Try this link:
[http://makuchaku.info/amnesty/#windows](http://makuchaku.info/amnesty/#windows)
If you can't work it out, ask again.[/QUOTE]


Thanks, that worked

---

