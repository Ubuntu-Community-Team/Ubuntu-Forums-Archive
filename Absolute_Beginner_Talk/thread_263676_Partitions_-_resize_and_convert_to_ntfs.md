---
title: "Partitions - resize and convert to ntfs"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-09-23
My ubuntu is in a 50 gb partition.
Win xp is in a 25 gb.
How can i split the 50gb one in half and convert it to ntfs to use as media storage space for win xp
(messed up when installing ubuntu I know!)

---

### Post by jd65pl on 2006-09-23
You could download gParted live cd and re partition the drive to give you more space.

You may like to consider reformatting as FAT32 as both windows and linux can read and write this file structure.

J

Edited: A mounted partition can't be re-sized

---

### Post by lamego on 2006-09-23
You will need to boot from a LiveCD and use the gnome partition editor to shrink your linux partition.
Then just create the ntfs partition on windows using the free CD .

---

### Post by drifternel on 2006-09-23
so if its fat 32 i can just drop files in (ie jpeg photos)from ubuntu and win xp and use them in either?

---

### Post by jd65pl on 2006-09-23
Yes both operating systems are able to use the partition. e.g you would be able to play your mp3s in both windows and Linux. Or download documents using linux, save them to your FAT32 part and then boot windows and edit them.

Cheers

J

---

### Post by drifternel on 2006-09-23
nice one, sound like a good solution
ok so which will be the easiest way to repartition without risking killing my set up?

---

### Post by drifternel on 2006-09-23
ive shrunk the linux partition down with gparted.
Seems ok but it wont now let me convert the unallocated space to fat 32 as it says there can only be a max of 4 primary partitions,
the 4 are ntfs linux linux swap and 10mb
it says i need to creat an extended partition but how???
any ideas

---

### Post by meng on 2006-09-23
Something like this:
select the unallocated space
create new partition - extended (not primary)
now create a new logical partition within the extended partition - you can use all the space if you only want one more partition
That should do it.

---

### Post by bulldog on 2006-09-23
Poehhhhh you can ask things I have to think about.:D 

If I remeber correctly,if you want to make an extended partition you can only have three primary's,but I could be wrong there.

So you could delete your swap as primary and create an extended partition and create a new swap within.
The rest you can make a Vfat or what ever you want.

---

### Post by drifternel on 2006-09-23
both gparted and windows disk management are not giving me the option to do anything with the unallocated space
is it because there are already 4 partitions?
Can i delete the linux swap partition, then create an extended partition with the unallocated space?

---

### Post by bulldog on 2006-09-23
Think so yes,you only have to create a new swap within the extended partition.

The disk you are managing ** must be unmounted **

---

### Post by drifternel on 2006-09-23
excuse my ignorance bulldog but what does unmounted mean!

---

### Post by bulldog on 2006-09-23
To read your hdd you mount it,in most cases Ubuntu does that automaticly.

But when you want to resize or what ever your hdd should not be mounted because you can't change anything.

There must be an option somewhere,or you even get a message,that you need to unmount the drive before your actions can be aplied.

---

### Post by drifternel on 2006-09-24
I've tried to use gparted but it wont do anything with the unallocated space as it says that there can be no more than 4 primary partitions.
I then tried to delete the linux swap file but it still wont let me do anything with it for same reason.
Any ideas folks?
Ive attached a screenshot if that helps.

---

