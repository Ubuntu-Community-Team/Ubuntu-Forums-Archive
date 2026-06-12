---
title: "Stupid HFS+"
date: 2007-07-25
forum: Apple Intel Users
---

### Post by ivesjd on 2007-07-25
I have a shared HFS+ partition that I share everything thing between OSX and Ubuntu. I at one point had it working, then after a reinstall I cant seem to get write access to it from Ubuntu. At first I thought it was the mount options I had in fstab, So I changed them to defaults, booted into OS X to make sure I had permissions set to "Others: Read & Write" and the journaling was turned off. But I still dont have write access. When I try to chown the /mnt/Media or any files in it, I get read-only file system. Does anyone have any ideas?

---

### Post by benanzo on 2007-07-25
If you want to have write access to the OS X filesystem you'll have to disable journaling and mount the partition as root.

to automatically mount your OS X paritition when you start Ubuntu:

Make a directory for the OS X partition to mount into:
```
sudo mkdir /mnt/osx
```

Open the Filesystem Table (/etc/fstab) for editing as the root user:
```
sudo gedit /etc/fstab
```

Add this line to the end of the file:
```
/dev/sda2 /mnt/osx hfsplus user,defaults 0 0
```

**/dev/sda2** is the name of the OS X partition to mount.
**/mnt/osx** is where you want the partition to mount to.
**hfsplus** is the type of filesystem the partition is (HFS+)
**user,defaults** these are the options to set when mounting the partition.  "user" lets non-root users mount it.
**0 0** don't worry about these (they're used for backing up and filesystem checking)

If you want to be able to write to the OS X disk from Ubuntu you'll need to disable journaling from within OS X and mount the partition as root in Ubuntu.

To disable journaling in OS X:
Open a terminal and type:
```
diskutil disableJournal disk0s2
```

Or use Disk Utility.

Good Luck!

---

### Post by ivesjd on 2007-07-25
I've done everything that you said and I still don't have write access. I did this a few weeks ago but then I reinstalled and now I cant get it to work. This partition is not actually the OS X partition but it is my shared partition. (Read on here that HFS+ was a good way to go) I COULD reformat the partition as ext3, but I would prefer not to. And I dont want to use FAT32 for file size limits. Anyone have any ideas? I was thinking maybe reformat it as HFS+ again incase something was wrong with it. But it works fine in OS X.

---

### Post by cyberdork33 on 2007-07-25
> **ivesjd said:**
> I've done everything that you said and I still don't have write access. I did this a few weeks ago but then I reinstalled and now I cant get it to work. This partition is not actually the OS X partition but it is my shared partition. (Read on here that HFS+ was a good way to go) I COULD reformat the partition as ext3, but I would prefer not to. And I dont want to use FAT32 for file size limits. Anyone have any ideas? I was thinking maybe reformat it as HFS+ again incase something was wrong with it. But it works fine in OS X.

Filesystem errors?

---

### Post by ivesjd on 2007-07-25
So its now mostly working. What I did was enabled journaling and then disabled it. And also checked the ignore permisions on this volume. Since its shared I figured why not. And I am the only one who uses this computer. Now for the mostly working part, if I move a file (i.e. click and drag) it doesn't move it but copies it.

---

### Post by benanzo on 2007-07-26
I think copying is the default action when moving a file from one filesystem to another.

---

### Post by ivesjd on 2007-07-26
It copies even within the same filesystem. As in from the top of that partition tree into a folder in that tree.

---

### Post by ronocdh on 2007-07-26
> **ivesjd said:**
> It copies even within the same filesystem. As in from the top of that partition tree into a folder in that tree.
Very interesting and certainly not the desired functionality. I too had journaling disabled and sharing worked fine, but on a reinstall, things we different. I believed I cleared things up with a **sudo nautilus** and switched all the permissions in Ubuntu to what I needed. I understand that this is a messy method, though, but it did do the trick for me.

---

### Post by Gen2ly on 2007-07-26
Definitely sounds like a permission problem.  I tripped upon a problem following a reinstall.  Though my username, localhost... were the same, the permissions of the files in the DVD were a cryptic group number.  Have you set ownerships to the files recursively?

---

### Post by benanzo on 2007-07-27
You might end up with some permissions problems on the files in OS X, but you could certainly try chowning everything in that filesystem to your Ubuntu user:

Move to the top of your HFS+ directory and do:
```

sudo chown -R <your username> ./*

```

---

