---
title: "Data recovery from ext3 partition"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by halon on 2008-01-24
I am using a Lacie 250gb external hard drive to back up data.  The disk was formatted with gparted and the entire disk is ext3. When I try to view the contents of the drive /media/disk
all I get is a lost and found folder.

The good news is that the folder is roughly the size of the backup data I lost, so I assume the data is there and in good shape, I simply cannot read it.

Can anyone recommend a good way to get this data back??

Thanks

---

### Post by skymera on 2008-01-24
you want a way to access Lost+Found?

well

```
 sudo nautilus /media/disk 
```
thn try

---

### Post by Herman on 2008-01-24
Hello halon,
Recovering files from the lost+found is an interesting subject, it's hard to find very much good information about it. 

skymera's solution sounds like a great idea.

Here is the best document I have found yet on the subject of recovering data from the lost+found directory, it's a .pdf file,  [http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf](http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf), just in case it's useful at all.

I think  that 'sudo nautilus /media/disk' will be the award winning way to get started with it though. That might lead to an easier way to achieve the same outcome as the process I linked you to. I can't see anything on that document to show when it was last updated, or even the date it was published.  I haven't any personal experience in this, so I will be interested to read how you get along.

Regards, Herman :)

---

### Post by halon on 2008-01-24
Thanks to both of you!! Ill try it and see  what I get.

---

