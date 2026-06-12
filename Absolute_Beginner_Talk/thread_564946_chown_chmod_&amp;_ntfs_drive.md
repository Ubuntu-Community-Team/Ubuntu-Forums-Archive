---
title: "chown chmod &amp; ntfs drive"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by gordonh on 2007-10-01
Hi,

I've been messing around with my windoze drive from which I deleted all windows rubbish a few weeks ago.

recently it's been showing as full in gparted, but there was only about 5 gigs on it visible through places (it's about 47 gig).

Now the real problem.  I umounted and remounted using gparted and now root is the owner.  I've used chown and chmod to change first ownership, then modes.  The dialogue shows ownership and modes being changed but places ignores this and still shows owner as root and permissions unchanged (ls -l shows the same thing)

incidently, both chmod & chown show that they are changing thousands of files with the pattern ./.trash-gordon/... and I would be happy to delete them using the command line, but all flavours of dir & ls don't find them.

I've tried loading nautilus as root from the command line, so that I can change permissions, but the response is "cannot open Display"

help please.

---

### Post by Pumalite on 2007-10-01
Check it with rescuecd; it's probably corrupted:[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by bodhi.zazen on 2007-10-01
You can mount with read-write access with ntfs-3g, ntfs-config is a gui front end for ntfs-3g :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Otherwise you set ownership and permissions at the time of mount :

sudo mount -t ntfs-3g /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=000

See this link (yea, it is on fstab, but it will go through some of this)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by gordonh on 2007-10-01
trying that thanks.  I'll let you know the results

---

### Post by gordonh on 2007-10-01
> **bodhi.zazen said:**
> You can mount with read-write access with ntfs-3g, ntfs-config is a gui front end for ntfs-3g :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Otherwise you set ownership and permissions at the time of mount :

sudo mount -t ntfs-3g /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=000

See this link (yea, it is on fstab, but it will go through some of this)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

tried the sudo mount with the same results.  I'll try the rescuecd option

---

### Post by bodhi.zazen on 2007-10-01
did you install ntfs-3g ?

---

### Post by gordonh on 2007-10-02
> **bodhi.zazen said:**
> did you install ntfs-3g ?

Yes.  I've been using the drive as my main data drive for months.   The only problem WAS that it acted full but looked empty.  the ./.trash-gordon all over it was the real issue, but the first I was aware of it was when using chown

---

### Post by gordonh on 2007-10-02
fixed.

downloaded systemrestorecd.

couldn't open it because it's downloaded to my windoze disk.

went to the firefox download window and clicked "all files downloaded to" and nautilus happily opened it.

checked permissions and it's MINE.

my only remaining problem is that the disk is stilled clogged with ./.trash-gordon* files and I cant see them.

where/how do i find and delete these things (nb my wastebasket is empty)

Thanks guys.

---

### Post by jw5801 on 2007-10-02
```
ls -a
``` will show it to you. Anything with a period at the start of the name is a hidden file in Linux. Try pressing ctrl+h in nautilus in your home folder and you'll see a lot of hidden files that are all your settings and stuff for programs. If you want to remove the "trash" folder, then use: ```
cd /*diskmountpoint* #replace with whereever your disk is mounted
sudo rm -rf .trash-gordon
```
GNOME defaults to adding a "trash" folder whenever you delete things on a drive (that doesn't contain your home directory) using nautilus. So that folder will contain everything that was on the drive that you deleted.

---

### Post by gordonh on 2007-10-02
Excellent.  It'll take a while to re-delete everything (especially as some of it was only deleted to make space)

Thanks everyone.

---

