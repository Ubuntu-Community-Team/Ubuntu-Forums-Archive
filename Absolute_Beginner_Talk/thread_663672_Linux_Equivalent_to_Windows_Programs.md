---
title: "Linux Equivalent to Windows Programs"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by monsieurdozier on 2008-01-10
I was wondering what are some good Linux native equivalents to the following Windows programs:

chkdsk
Defrag
Eraser (A secure deletion program)
and
Restoration (A deleted file restoration program)

I would prefer anything that I don't have to compile myself.

Thanks much.

Monsieur Dozier

---

### Post by zach12 on 2008-01-10
You don't need a Defrag program on linux

---

### Post by mcduck on 2008-01-10
> **monsieurdozier said:**
> I was wondering what are some good Linux native equivalents to the following Windows programs:

chkdsk
Defrag
Eraser (A secure deletion program)
and
Restoration (A deleted file restoration program)

I would prefer anything that I don't have to compile myself.

Thanks much.

Monsieur Dozier

fsck would be the equivalent of chkdisk. It should check your partitions automatically every 30 boots. There is no need for defrag, as Linux filesystems don't suffer from fragmentation.

---

### Post by monsieurdozier on 2008-01-10
> **mcduck said:**
> There is no need for defrag, as Linux filesystems don't suffer from fragmentation.

Now that's just wonderful.

What about a secure file deletion program and a file restoration program?

---

### Post by cb951303 on 2008-01-10
wipe.sf.net ->  seems to be a secure deletion program

---

### Post by eolson on 2008-01-10
Unlike windows which really doesn't delete a file,  just flips one bit and the file system thinks the file is gone, linux/unix systems really do delete it.    So recovery is not that easy.

There are some "secure" delete programs around but can't think of them off the top of my head.

---

### Post by edm1 on 2008-01-10
If you're paranoid about secure deletion use 'shred' instead of 'rm', thats only command line though. You could easily create a nautilus script, or you may be able to find one, if you wanted to do it by right clicking. Why do you need a recovery program? I dont know if there are any. Usually those using linux are computer-savvy enough to not delete anything they want to keep and make backups of anything important to them.

---

### Post by legatek on 2008-01-10
I suppose you could use the dd command to overwrite your file/directory with random numbers, thus securely deleting it.

```
dd if=/dev/urandom of=/directory/series/file
```

To delete a bunch of files at once, move them to a directory and perform the above operation on the directory. No recovery though, so double check what you're deleting.

---

### Post by Odd-rationale on 2008-01-10
To securely delete files, you can use this nautilus script:
[http://www.gnome-look.org/content/show.php/shred_file?content=66603](http://www.gnome-look.org/content/show.php/shred_file?content=66603)

Download the file and extract it. Then put the "shred_file" script in the ~/.gnome2/nautilus-scripts directory. Restart nautilus, then you should be able t execute the script from a right-click context menu.

The problem is, it is pretty secure. You won't be able to recover the files you shred.

---

### Post by monsieurdozier on 2008-01-10
> **edm1 said:**
> If you're paranoid about secure deletion use 'shred' instead of 'rm', thats only command line though. You could easily create a nautilus script, or you may be able to find one, if you wanted to do it by right clicking. Why do you need a recovery program? I dont know if there are any. Usually those using linux are computer-savvy enough to not delete anything they want to keep and make backups of anything important to them.

I think shred should work, and I'll see about that script.

I never use a restoration program to actually restore things.  I use it to make sure things are deleted sufficiently.

Thanks everyone for your help.  I discovered I don't need any of these programs, Linux does it for me.

Thanks much,
Monsieur Dozier

---

### Post by edm1 on 2008-01-10
To feed the paranoier more...the alternate cd is now able to encrpt the entire or parts of the hard-drive during installation.

---

