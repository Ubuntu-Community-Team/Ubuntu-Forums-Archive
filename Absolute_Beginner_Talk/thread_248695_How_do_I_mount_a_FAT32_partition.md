---
title: "How do I mount a FAT32 partition?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-09-01
I just shrunk my ext3 partition using a GParted Live CD, creating about 15GB of unformatted space, which I then formatted to FAT32.  So I now have a brand-new 15GB FAT32 partition.

But I have no idea how to mount it.  In System -> Administration -> Disks, it's listed as hdb3, but is inaccessible.  When I click "Enable", the window just blinks as if it's refreshing, but nothing happens (no error messages or anything).

Where do I go from here?

Thanks for any info you may have!

---

### Post by Uluen on 2006-09-01
Did you select an empty folder to mount it in before clicking "enable"?

---

### Post by MiCovran on 2006-09-01
I had the same problem, only with NTFS partition. It's pretty simple, actualy.
Take a look at [this]("https://help.ubuntu.com/community/MountingWindowsPartitions#head-7036f2492d04f1d0984017ad8e71af0eda2690d6") page.

---

### Post by mjpatey on 2006-09-01
Uluen, thanks for the suggestion!  It's now mounted.

Unfortunately, I can't write to it because I'm not the "owner" of it.  I just looked at permissions for the folder I mounted it to, and I have to be "root".

Normally I'd get around something like this by adding "sudo" before a command and typing my password... but I don't know the Terminal command for this operation.

Anybody know how I get in and change permissions to allow anyone to write to my new FAT partition?

---

### Post by taurus on 2006-09-01
> **mjpatey said:**
> 
Anybody know how I get in and change permissions to allow anyone to write to my new FAT partition?
Just add this line to the end of your /etc/fstab and all is good...

```

/dev/hdb3   /media/share   vfat   defaults,umask=0000   0   0

```
assuming you have /media/share...  If not, create it with

```
sudo mkdir /media/share
```
And just in case you ask how to edit your /etc/fstab, open a terminal (Applications -> Accessories -> Terminal) and type

```
gksudo gedit /etc/fstab
```

---

### Post by mjpatey on 2006-09-01
What Taurus suggested almost worked... except I still don't have permisison to write to the partition, for some reason.  Could it be the formatting of the line added to fstab?  The zeroes in the line of code are spaced strangely, which for all I know could be right, but I wonder if it's the source of the trouble.

Anybody know how to make my FAT partition writable by anyone (or at least a non-root user)?

Thanks!

---

### Post by mjpatey on 2006-09-01
Guess what... I just rebooted, and now it works!

I rebooted into Windows first, to see if it recognized the new partition.  It did, but needed to be restarted for it to be completely installed.  After reboot into Windows, I was able to copy files to the partition from Win.  Then I rebooted into Ubuntu, and magically, I was not only able to access what I'd copied from Windows, but I copied files to it in Ubuntu as well!

It's now exactly what I need it to be.

Thanks for the help, everyone!

-Mark

---

