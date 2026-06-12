---
title: "Backup/Imaging a XP:Linx Dual Boot"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by lmzrsk on 2008-01-08
I'ma new linux user.  As an XP user, I'm used to imaging my system once a month as a sefety.  I've used Acronis and Norton Ghost.  Both a simple and stright forward.  Image the whole drive - restore the drive.

I've partitioned my hard drive into a linux partition and XP, using the default installation settings from the live ubuntu cd

I'm looking for some advice on backing/imaging this dual boot system, so that once the system is restored, it is functional without any further intervention.  I don't want to have to use the super grub cd, or rescue cd.  I've no interest in backing up partitions.  I just want to do the drive.

I'm asking because I've read some posting that suggest that grub does not survive a Ghost or Acronis restore.

I'm looking for more than a software recommendation.

Can anyone point me at a tutorial on how I can do this?

Thanks

---

### Post by p_quarles on 2008-01-08
Are you looking for something like this?
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by lmzrsk on 2008-01-09
Thanks very much
But all the page link refers to is backing up a partition. Nothing on a drive.
And, the site shows that XP NTFS is not fully supported.

I'll have to keep looking
Thanks

---

### Post by kpkeerthi on 2008-01-09
Try ghost for linux: [http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml](http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml)

---

### Post by LaRoza on 2008-01-09
I use Clonezilla, see the link in my sig.

---

### Post by julian67 on 2008-01-09
+1 for Clonezilla. Direct link to Clonezilla-GParted CD: [http://gpartedclonz.tuxfamily.org/]("http://gpartedclonz.tuxfamily.org/")

This one CD is everything you need for making partitions/managing disks (GParted) and cloning drives or partitions (Clonezilla). Clonezilla, like Norton Ghost or Acronis, will make an easily restorable image of the entire disk if you like and will not waste time backing up unused sectors, so it's fast (G4L aka Ghost 4 Linux copies all sectors, used or unused, so can be incredibly slow).  It handles all the Windows filesystems as well as the Unix/Linux ones so it will easily clone your NTFS/FAT partitions, the mbr etc. It's thoroughly reliable and when making the restore you can choose to restore the whole disk or just selected partitions. It uses partimage but with enhancements, making it easier and more versatile.  Essential tool!

---

### Post by lmzrsk on 2008-01-09
Everyone,

Thanks very much for all you input.  It looks like Clonezilla is the way to go for a simple backup/restore drive requirement.  I''m downloading and will give it a go.

I finally heard back from Acronis as well.  Acronis 9+ will also image a disk and restore it, including MBR and GRUB.  SO, if all else fails, I have a backup plan.

Thanks again.

lmzrsk

---

### Post by julian67 on 2008-01-09
> **lmzrsk said:**
> Everyone,

Thanks very much for all you input.  It looks like Clonezilla is the way to go for a simple backup/restore drive requirement.  I''m downloading and will give it a go.

I finally heard back from Acronis as well.  Acronis 9+ will also image a disk and restore it, including MBR and GRUB.  SO, if all else fails, I have a backup plan.

Thanks again.

lmzrsk

Yes Acronis will do the same task, but in my experience rather slowly. And the GUI is really designed for showing Windows partitions. You might have multiple Linux partitions on a drive but Acronis's GUI assigns them letters like Windows does...it makes it a little confusing.  Clonezilla isn't pretty but it is faster at perfroming the identical task and you always know which partition is which...no need for  mental translation that / is C and /home is D etc

---

