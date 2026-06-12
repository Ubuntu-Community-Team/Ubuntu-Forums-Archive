---
title: "[SOLVED] In process of reinstall,  /home folder backup - problems with cd write and u"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-25
On buring to cdrw it saus some files will have to be truncated cos of 64 character joliet limit?

Trying on usb stick it says cant create symlinks.

Which option of backup will enable a full restore of home folder once reinstalled?

---

### Post by tszanon on 2007-09-25
> **philinux said:**
> On buring to cdrw it saus some files will have to be truncated cos of 64 character joliet limit?

Trying on usb stick it says cant create symlinks.

Which option of backup will enable a full restore of home folder once reinstalled?
Use tar to backup everything, then save the .tar file to cd/dvd/whatever.

Easy way: in Nautilus, go to your home folder. Then select everything that's important, then right-click it, select Create Package. Choose a good name for it, like home_backup :), choose the file type:
.tar: no compression, fastest
.tar.gz: some compression, slower
.tar.bz: good compression, even slower

There may be more options, but these are the basic ones. Any Ubuntu default installation will be able to decompress the resulting archive.

---

### Post by philinux on 2007-09-25
Under burn advanced I selected allow 103 length filenames woohoo in business

Should I have selected allow symlinks?

---

### Post by tszanon on 2007-09-25
> **philinux said:**
> Under burn advanced I selected allow 103 length filenames woohoo in business

Should I have selected allow symlinks?
If you're not planning on using this backup in windows, you can disable the Joliet extension. It will eliminate its limitations, like not supporting symbolic links. In my humble opinion, using these switches in the Advanced options are dangerous, because you are ignoring the limitations of the decisions you made before (like using the Joliet extension and saving symbolic links). If you won't use it in Windows, disable Joliet for now, since it does'nt support symlinks. If you find out you will need to use it under Windows, you'll still be able to read the files, but all filenames will be in the 8.3 format.

---

### Post by philinux on 2007-09-25
Attached screenshot shows options for filenames - cant ditch joilet until you click the burn button. So which option is best its my home folder I'm backing up so I'm preserving permissions too.

The symlinks are created when dragging and dropping by the way ?

---

### Post by philinux on 2007-09-25
bumpio

---

### Post by tszanon on 2007-09-27
I can't see the screenshots (probably because I'm at work). Since you can't remove the Joliet extension, just enable Rock Ridge (I believe it's already enabled) and allow symlinks. That should work fine.

---

### Post by philinux on 2007-09-27
backep up to pen drive- no probs

---

