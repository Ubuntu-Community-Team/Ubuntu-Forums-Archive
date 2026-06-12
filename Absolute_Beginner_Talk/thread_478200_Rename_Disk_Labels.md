---
title: "Rename Disk Labels"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-06-19
Hi:

I have some NTFS hard drives, mounted using ntfs-3g, whose labels I would like to change.  How can I do this? (I should note that they were named used Windows XP).

And bear in mind when giving an answer that I am still a n00b in Linux, so please give instructions step-by-step.

Thanks in advance,
LK

---

### Post by mahiyar on 2007-06-19
The best way I can tell to change disk labels is to go in Windows (since the partition is NTFS you are in dual boot I presume) and change the disk label  by right clicking the drive letter or whatever.

---

### Post by LordKelvan on 2007-06-19
That is true - but I wanted to learn how to do it in Linux.  Anyone know how?

---

### Post by bodhi.zazen on 2007-06-19
Like this :

[http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label](http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label)

Scroll down to FAT/NTFS section

---

### Post by LordKelvan on 2007-06-19
Hi:

Thanks - I just have a question about that article:

In my fstab file I already have entries (which ntfs-3g put in I believe) which look very similar to the entry the article told me to add, except my lines begin with UUID = <some number>.  So should I just change the beginning of the lines from UUID=<some number> to LABEL = <my label>, or should I add the line like it says in the article?

Cheers,
LK

---

### Post by bodhi.zazen on 2007-06-19
You can use :

UUID=xxx
/dev/yyy
LABEL=zzz

Any and all formats should work. Ubuntu is migrating to UUID over /dev/

---

### Post by LordKelvan on 2007-06-19
Hmm, let me make sure I understand what you are saying:

All I have to do is use ntfslabel to change the label - I don't have to make any changes to the fstab file (since changing the label of a drive will not affect its UUID, and so the fstab file, as it currently is, is still valid)?

---

### Post by bodhi.zazen on 2007-06-19
> **LordKelvan said:**
> Hmm, let me make sure I understand what you are saying:

All I have to do is use ntfslabel to change the label - I don't have to make any changes to the fstab file (since changing the label of a drive will not affect its UUID, and so the fstab file, as it currently is, is still valid)?

Yep. If you change the label and are mounting with UUID you will be good to go. almost begs the question of why change the label ? most change the label to mount by label.

The UUID only changes when you wither set one or re-format the partition.

---

### Post by LordKelvan on 2007-06-19
Well right now the 3 disks + 1 partition are displayed on my desktop as sda1, storage 1, storage 2 and storage 3, which really aren't the most descriptive of names (yeah I know, I wasn't really thinking when I named them in Windows).  Just wanted to change the labels for that reason.

---

### Post by bodhi.zazen on 2007-06-19
Awesome reason :)

---

### Post by mahiyar on 2007-06-19
Something to learn for me today - Change labels in Linux. I was mortally afraid of changing labels because I have "heard" instances of people wiping out data using wrong commands while changing labels.

---

