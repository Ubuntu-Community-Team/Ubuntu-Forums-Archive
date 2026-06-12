---
title: "sharing ext drives with windows ? ? ?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by guest5 on 2006-09-08
if i desire to share music on drives to other computers, do have to set up a server, and dose that server get in the way of me being a workstation equivalent?

i am sorry but i don't understand the concept yet.

---

### Post by kidders on 2006-10-03
Hi there,

I'm not sure I follow exactly what your question is, but there's no problem serving files to other computers. If you want to share with Windows, just install Samba.

---

### Post by pay on 2006-10-03
You can just install the ext3 driver for windows and then it will be allowed to read/write to that drive. Linux can also natively read/write to fat32 partitions. [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by kidders on 2006-10-04
Hi again,

> if i desire to share music on drives to other computers
Unfortunately, a windows driver for the Linux extended filesystems won't help you if you want to share files with other computers. When sharing files over a network, the filesystem in use on the server is largely irrelevant. Samba is you best bet, I think.

---

### Post by Aberrix on 2006-10-04
> **pay said:**
> You can just install the ext3 driver for windows and then it will be allowed to read/write to that drive.[http://fs-driver.org/](http://fs-driver.org/)

it says for ext2, will it work the same for ext3?

---

### Post by kidders on 2006-10-04
Ext3 is just journalised Ext2, so you shouldn't have problems ... except that your filesystem journal won't be kept up to date. You're sharing your files between different operating systems on the same computer, by the sound of it.

[http://fs-driver.org/faq.html#acc_ext3](http://fs-driver.org/faq.html#acc_ext3)

---

### Post by Aberrix on 2006-10-04
> **kidders said:**
> Ext3 is just journalised Ext2, so you shouldn't have problems ... except that your filesystem journal won't be kept up to date. You're sharing your files between different operating systems on the same computer, by the sound of it.

[http://fs-driver.org/faq.html#acc_ext3](http://fs-driver.org/faq.html#acc_ext3)

*Sorry, hope I am not thread jacking*

Yeah, I've got a 'storage' drive that i'd like to use for file storage/sharing between XP and Ubuntu (still trying to get away from Windows). Nothing but data on on the drive, however its important stuff and I don't want to risk losing/corrupting anything.

Would formatting my storage drive to Ext2 (or Ext3?) then using the fs-driver for windows be a good/safe choice for me?

---

### Post by kidders on 2006-10-04
I guess so. What filesystem are you using at the moment?

It seems as though the driver pay mentioned would ignore your filesystem journal, increasing the risk of corruption in the event of an unclean shutdown (which, if memory serves, is the only kind of shutdown a Windoze user can ever expect to perform lol!).

My personal preference when sharing data between operating systems on the same PC is to use a filesystem well-supported by both environments. Unfortunately, as pay will no doubt agree, resorting to FAT32/NTFS comes with a serious downside :-(

**Edit:** Regardless of how you choose to store the files though, there is no substitute for regular backups!

---

### Post by Aberrix on 2006-10-04
> **kidders said:**
> What filesystem are you using at the moment?

I am still bringing things up and configuring them so my 'storage' drive isn't actually connected yet. I have NTFS on my XP drive, and default Ext3 with my Ubuntu drive.

Currently my 'storage' drive is NTFS. But last time I played with Linux (2 years ago), NTFS was able to read but not write and was very unstable and usually ending in corruption...

I remember being able to read/write with FAT32 on linux. Would this be a better solution? pending Linux plays okay with FAT32.

This 'storage' drive contains music, movies, pictures and (windows) install files.

My main concern is stability, if that means FAT32 I am cool with that...

What do you think?

---

### Post by kidders on 2006-10-04
Your NTFS information is still current, I'm afraid. Writing with Linux's reverse-engineered driver isn't considered "safe" yet. The trouble with FAT32 is that it's badly designed ... it's damn slow, fragments terribly, and has no concept of ownership/permissions, which would discourage _me_ from *ever* using it :-(

If you don't mind the downside, FAT32 is your best bet, imo. It has native Windows support and is considered very reliable in Linux.

I hope that helps.

---

### Post by Aberrix on 2006-10-04
> **kidders said:**
> The trouble with FAT32 is that it's badly designed ... it's damn slow, fragments terribly, and has no concept of ownership/permissions, which would discourage _me_ from *ever* using it :-(

If you don't mind the downside, FAT32 is your best bet, imo.

From what it sounds like it would be a pretty good solution for me...

- I don't care much about the speed, its file storage *shrugs*
- I can deal with fragmentation/defragmentation
- Ownership/Permissions isnt a big deal either, nothing sensitive or worth worrying about.

---

