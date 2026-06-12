---
title: "Upgrade to gutsy, now ntfs fails"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-02
Gutsy sees my three windows partitions, but cant mount them.  They work on live disk but not on my installation.

I tried to force and it says the devices are busy and had an unclean shutdown and i should reset my $logfile. help?

---

### Post by rudeboyskunk on 2007-11-02
There's an ntfs package you have to install.  Go to System>Administration>Synaptic Package Manager and search for "ntfs."

---

### Post by Evil Wayz on 2007-11-02
> **rudeboyskunk said:**
> There's an ntfs package you have to install.  Go to System>Administration>Synaptic Package Manager and search for "ntfs."


did that. now it shows ONE out of the three, and i cant mount the other two because i am not privileged. GAH

---

### Post by rudeboyskunk on 2007-11-02
> **Evil Wayz said:**
> did that. now it shows ONE out of the three, and i cant mount the other two because i am not privileged. GAH

That shouldn't be a problem.  Go to a command line and type:

```
$ sudo mount /dev/sd* /mnt
```

Where * is the letter of the hard drive you want to mount (a, b, c, d, etc).

---

### Post by Evil Wayz on 2007-11-02
> **rudeboyskunk said:**
> That shouldn't be a problem.  Go to a command line and type:

```
$ sudo mount /dev/sd* /mnt
```

Where * is the letter of the hard drive you want to mount (a, b, c, d, etc).

how do I determine the linux name for the drive? Said devices didn't exist when i tried that command.

im getting that unclean shutdown dialog when I do that code.

edit:

looks liek this:

wolf@wolf-alteredbeast:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 (Lycanthrope)
wolf@wolf-alteredbeast:~$

---

### Post by Adramelech on 2007-11-02
actually gutsy uses ntfs-3g you have to mount ntfs drives with

ntfs-3g /dev/my_disk  /media/my_disk

remember to create the /media/my_disk folder first.

Your 2 drives are marked as unclean, linux cant fix this ntfs flag, boot in windows and shut the computer down correctly and the drives will be marked as clean.

---

### Post by Evil Wayz on 2007-11-02
> **Adramelech said:**
> actually gutsy uses ntfs-3g you have to mount ntfs drives with

ntfs-3g /dev/my_disk  /media/my_disk

remember to create the /media/my_disk folder first.

Your 2 drives are marked as unclean, linux cant fix this ntfs flag, boot in windows and shut the computer down correctly and the drives will be marked as clean.

That worked. Now to try and unfuxxor my dual screen problems.  :)

---

