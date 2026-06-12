---
title: "HFS+ Stuff Up :( Doh!"
date: 2007-09-28
forum: Apple PPC Users
---

### Post by tsufi on 2007-09-28
Hi there. Really need some help here if anyone is good with solving hard drive stuff-ups!

I've have a new 500GB external hard drive which I posted to a friend in another city so that he could put some important files on. I was using Vista and he was using a MacBook Pro.

Of course since the hard drive was new ... he formatted the hard drive under the standard HFS+ (with journaling) ... then he put the files on and posted it back to me.

Now when I received the hard drive I installed it under Vista but of course the file system couldn't be recognised and thus no drive showed up. I then clicked on My Computer -> Manage -> Disk Management where I could see that "Disk 1" (my external hard drive) was there but of course unrecognised.

I ACCIDENTALLY clicked an option which gave it a MBR (Master Book Record) at the beginning of the hard disk's sectors and assigned it to Drive F: ... but it didn't format the drive because I knew that'd wipe the files.

Knowing that Vista has no HFS+ support whatsoever, I quickly installed my Ububtu Studio 7.04 on a separate partition on my laptop's hard drive (knowing of course that Linux has better power to fix such problems than Windows).

Now when I go to System -> Admin -> GNOME Partition Editor (GParted) .. it tells me that /dev/sdb (which is my 465 GB external hard disk) has an unknown Filesystem.

When I go to terminal and type in fdisk /sda/sdb -p I get:

```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    6  FAT16
```

I think FAT16 shows up because of what I did under Vista by adding the MBR accidentally ... even though that I KNOW all the files are still on the hard drive. However .. they are all unaccessible because the HFSPlus header has gotten corrupt somewhere along the way :(

Can anyone help? (Without suggesting me to reformat and send the hard drive back for my friend to copy the files back? :P)

Thanks!

---

### Post by Lo'oris on 2007-09-29
[COLOR="White"]if, and I repeat IF, the only changes in the disk are in the partition table, then a simple solution I once used was to use fdisk to delete that partition, and create a new one of the desired type.

fdisk simply changes the partition table, without formatting nor anything else.

so IF there were no other changes, everything should go well.[/COLOR]

but that's a sort of thing I did only once, and I'm not sure if it applies to you too, so my advice is to wait for a reply by someone who knows better, and then **do as I did if AND ONLY IF it's your very last option**. I take no responsabilities : P

---

### Post by tsufi on 2007-09-29
Hey thanks for the post :)

Never mind ... I just solved the problem less than a couple of hours ago by installing R-Studio v4.0 in Vista.  Its amazing software which recognizes nearly all major file systems and lets you back it all up, even stuff that got deleted!

---

### Post by Lo'oris on 2007-09-29
gg, you got lucky :)

out of curiosity, what kind of big and important data did you need to use this unusual transfer method?

---

