---
title: "backup/partition worries/advice"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by neoni on 2008-03-14
hello friends

i'm running xp currently, and am trying to partition my drive. [_[COLOR="Red"]windows defrag gives me 'unmovable files' almost all over my drive[/COLOR]_]("http://img338.imageshack.us/img338/7785/94638082ei1.jpg") so i'm worried that this will mess up my OS. i have backed up all files and settings, but i don't have an xp disk to boot from, because my laptop just has a hidden partition which (i assume..) is the backup stuff. i'll use gparted unless somebody can suggest something better (not keen on paying, being a poor student)

is it really likely partitioning will kill my windows?
will i be able to boot easily from the hidden partition on the laptop?

if the answer to those are yes/no respectively, how can i make a boot disk?


looking forward to joining the ranks again \\:D/

---

### Post by forestpixie on 2008-03-14
often in the past I have found that a lot of the unmovable files are related to old system restore points - if you've got it turned on and haven't a problem doing so - turn it off

try defragging again and see what occurs then

also you could, if you've got a good amount of RAM turn off the pagefile and defrag

---

### Post by neoni on 2008-03-14
that helped with the defrag - there's still one wee bar towards the end of the drive though, will that mean that windows wouldn't boot i, say, halfed the size of the partition?

i've never partitioned a drive so i don't know how it really works

---

### Post by neoni on 2008-03-14
will partitioning push stuff to the side that isn't getting deleted, or will it just chop it off?

i'm having very little luck finding out how it works on google :confused:

---

### Post by maniac_X on 2008-03-14
> **neoni said:**
> will partitioning push stuff to the side that isn't getting deleted, or will it just chop it off?

What you will be doing is shrinking down part of the Windows partition with GParted. The GUI is fairly self explanitory. You will click on the Windows partition and grab it at the right side and slide it over. You are going to want to shrink it probably about 15GB or more depending on if you plan on just trying out Ubuntu for now or staying in for the long haul. Once you commit to the changes, GParted will handle all the file moving chores for you. Once you have made room on the drive, you can then install Ubuntu by letting it ** use the available space**(not the entire harddrive) for installation. Be sure to double check your choice during the installation phase as this is where most first timers make mistakes and let Ubuntu wipe the entire drive. There will be several installation choices, read each carefully.

1.) You will **NOT** want Ubuntu to use the entire drive for install. Only use the available space after shrinking the Windows partition down some.

---

### Post by maniac_X on 2008-03-14
I recommend you get and burn the [GParted Live CD]("http://gparted-livecd.tuxfamily.org/") or [PartedMagic Live CD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads") and boot it and just look around but don't commit to any changes. This way you will have an idea of what to expect during the install procedure of Ubuntu.

---

### Post by iansane on 2008-03-14
Don't know if gparted is better (safer) but I've always heard that even though not real likely, it is possible for data corruption from resizing and that you should be sure to backup important files before resizing. Also I may be wrong but I think you have to use a boot floppy to run restore from recovery partition if recovery becomes nessesary.

---

### Post by Forrest Gumpp on 2008-03-14
@neoni

See if this post is any help:  [http://ubuntuforums.org/showpost.php?p=4273424&postcount=12](http://ubuntuforums.org/showpost.php?p=4273424&postcount=12)

---

### Post by maniac_X on 2008-03-14
> **iansane said:**
> Also I may be wrong but I think you have to use a boot floppy to run restore from recovery partition if recovery becomes nessesary.

CD images(.iso image) of [Win98SE or WinMe]("http://www.allbootdisks.com/download/iso.html") will fit the bill, especially if no floppy drive is available. They may not work ofr Vista though, I don't have Vista so I can't check.

---

### Post by neoni on 2008-03-16
thanks guys!

everything went fine with the partition, and i am responding from ubuntu now :)

---

### Post by forestpixie on 2008-03-16
excellent - welocme back :)

can you mark thread solved then.

---

