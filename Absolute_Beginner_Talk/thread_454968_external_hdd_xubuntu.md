---
title: "external hdd xubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by diatribe on 2007-05-26
Ok I've read through a number of posts asking this same question, but I'll try for an answer again here.  I recently reinstalled feisty; I run a laptop with an external hdd (sdb1) formatted in vfat that I would like to mount on boot.  I have created the entry in fstab, and on boot it attempts to mount, says failed, and continues booting.  After the network configuration portion, though, right after it says sdb1 cant be mounted, it says sdb detected assuming write-through or something along those lines.  Now once I enter xfce, I can mount the device no problems.  I would like it to be mounted on boot though because I run mpd and this is where all my music is stored.  The relevant fstab line is below:

/dev/sdb1       /media/disk     auto    defaults,,rw,utf8,umask=007,gid=46 0 3

any help would be greatly appreciated

---

### Post by Ek0nomik on 2007-05-26
It's FAT32?

Make sure to create the directory:

```
sudo mkdir /media/disk
```

Then:

```
/dev/sdb1 /media/disk vfat defaults 0 0
```

---

### Post by diatribe on 2007-05-26
the directory exists, as I said it mounts fine once the DE has loaded.  I simply cant get it to mount at boot.  I can manually mount, mount -a works fine, /media/disk exists, /dev/sdb1 is the right path.  it just wont mount at boot, that is what I want.

---

### Post by Ek0nomik on 2007-05-26
Again, it's a FAT32 drive correct?

If so, give it "vfat defaults 0 0" attributes instead of what you have.

---

### Post by diatribe on 2007-05-26
Gvae it a try, still doesnt work.  On boot it says special device: /dev/sdb1 does not exist, almost immediately after says:

[   21.120000] sdb: assuming drive cache: write through

twice, then continues to boot.  The other odd thing I noticed is that although it doesnt mount at boot, it doesn't prompt me for the root pass, it brings me straight to GDM.

It still lets me mount he drive once I am into X windows; I am confused by why it won't mount at boot.  It's almost like it just needs another 10 seconds and then it would work fine.  Once in X:

ebirtaid@serenidad:~$ sudo mount /dev/sdb1
Password:
ebirtaid@serenidad:~$ sudo mpd
ebirtaid@serenidad:~$ 

Like I said it works fine once in X, just will not mount at boot.

---

