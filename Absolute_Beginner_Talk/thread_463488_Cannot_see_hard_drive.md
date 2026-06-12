---
title: "Cannot see hard drive"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Nezing on 2007-06-03
I have downloaded GNOME partition editor,and made my old drive of 71.64 GB,into a full linux-swap drive,having got rid of the Windows NTFS file system.Upon reboot of Ubuntu,I cannot find my old drive,except in the partition editor.What have I done wrong? :(

---

### Post by coffeecat on 2007-06-03
> **Nezing said:**
> What have I done wrong? :(

Nothing, but you need to [edit fstab]("http://www.psychocats.net/ubuntu/mountlinux") so that whatever partitions you have created are mounted for you.

But please tell me you haven't made one enormous swap partition of 71GB because that is what it sounds like. :( But don't worry if you have - it's soon sorted. :wink: Perhaps you could explain exactly what you have done, which drive the 'old' one is and what filesystems you formatted the drive with.

**Edit:** I'm afraid you won't get anything more from me for a few hours because it's late here in the UK atm and I'm going to bed soon.

---

### Post by Moop on 2007-06-03
Swap is similiar to the page file in XP. It's only used to hold data that doesn't fit in the memory. You don't need more that a 1gb swap partition. 
If you want to use the hdd for storage you just need to format it and then mount it.

---

### Post by Nezing on 2007-06-03
It's late here in the UK as well,and my "brain",is in meltdown.The drive I'm talking about,is my second,or "Reserve" drive,which I want to use to store media files on.It's /dev/hd1 ext 3 at the moment.What do I write in  Terminal? ](*,)
Sorry if I sound hopeless,but I've only been using Ubuntu for a few days.:(

---

### Post by drs305 on 2007-06-03
Please start by giving us the results of:
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
(that's a lower case L)

---

### Post by coffeecat on 2007-06-04
> **Nezing said:**
> Sorry if I sound hopeless,but I've only been using Ubuntu for a few days.:(

No problems. We've all been there.

If you give the information drs305 is asking for we'll soon get you sorted. Here's a tip. It might sound obvious but it doesn't occur to everyone and they end up laboriously typing terminal output into this forum's post reply field. Use the copy and paste function to copy the output of cat and fdisk - it'll avoid typos. As you're new to Linux, a word of warning - the copy and paste keyboard shortcuts in a terminal are different from the 'ordinary' ones you'll use in most apps like Firefox. Drop down the edit menu in Terminal and you'll see what I mean.

Another tip if you're also new to the forum tag codes. Enclose the output of fstab and fdisk in code tags like this:

>  {code}terminal output{/code} Except use square brackets where I 've used curly ones. It makes it easier to read, particularly for fstab where it preserves the spacing between fields which is important.

---

### Post by Nezing on 2007-06-04
This is my system (two harddrives-80 GB,and my "main" drive of 40 GB.I have followed the instructions given above,and this is what came out:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9337    74999421   83  Linux
/dev/hda2            9353        9728     3020220    5  Extended

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris

This what I get,after typing in the first code to Terminal:

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=9dae2448-efac-4628-89c1-351343a382b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=5cb953c8-ffa6-40b5-ba46-6ce18ace17dd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The second code just says invalid entry,if input seperate from first  code?
Oh dear,now I'm more confused than ever!!!

---

### Post by Nezing on 2007-06-04
***Panic Over***

Just looked in Places->Computer,and my "old" drive (Reserve),has now shown up.Thanks for all your help,it is appreciated.:popcorn: Now I can start adding my media files.
Cheers:guitar:

---

