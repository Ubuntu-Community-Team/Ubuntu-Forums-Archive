---
title: "moved files to unmounted harddisk"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by petri on 2006-01-28
and now they are disappeared. how can i get the files (catalogues) back?

---

### Post by ]Nbx*cmD[ on 2006-01-28
Just mount the device back:

```

sudo mkdir /mnt/myhd
mount /dev/hdXY /mnt/myhd

```

Where X can be a,b,c... representing your hard drive and Y is the partition number.
Ex. Your third partition of your secondary drive on IDE1 is called hda3

Hope it helps :p

---

### Post by Kimm on 2006-01-28
if the harddrive wasnt mounted when the files where moved, they shuold be in the folder you moved them to..

for example, if the harddrive mounts on /media/fat32 or something like that, they should be in that folder.

---

### Post by steve.horsley on 2006-01-28
Bear in mind that when you mount a drive, it **replaces** an existing directory. When you unmount it, the original directory is visible again This is not always obvious because it is customary to mount drives over empty directories, but it is the case. If you wrote files to a directory when there was no drive mounted there, then they should still be in that directory. If you can't see them because a drive has been mouted there later, then just unmount the drive again and you should see them.

---

### Post by petri on 2006-01-28
thanks guys, that sounds reasonable but it seems like i've made a bigger mistake. i have moved the files to a link that point/leads(?) to the earlier mounted drive. that link doesn't have any other catalogue or files. i have mounted the hd to the same catalogue, in this case: 
(hda(0,3)) /mnt/60 

unmounting and remounting the hd doesn't help.

it seems like the harddisk the catalogues were at the beginning is still as full as before moving the catalogues. so the files got to be somewhere in the original harddisk?

---

### Post by petri on 2006-01-28
thanks steve and the guys, now i've found them. gosh :rolleyes:

it seems like a link is something same as a catalogue. or a folder as it's called in english :)

---

