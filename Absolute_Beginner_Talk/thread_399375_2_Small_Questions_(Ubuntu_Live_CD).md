---
title: "2 Small Questions (Ubuntu Live CD)"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Poogy on 2007-04-02
Hi All,

I"m still in the evaluation phase, using the live CD in order to see whether ubuntu is right for my (rather poor) skills...
Currently there are 2 major problems I need to overcome in order to continue my evaluation:

1. _Network Issue_ - I've managed to share a folder over the network using SMB (I didn't configure anything, just let the OS work its magic using SMB, and chose to share the folder as a windows network share), however, when I try to access it from a windows computer in the network, I am prompted for a username password.
I've created a new user and tried to login from the windows machine using this user, but without success. I've given this user all privileges (again, using the GUI only), but still no success :-(

2. _File Access_ - Is it possible for me to access my existing windows files (NTFS) while running ubuntu from the live CD?

Many thanks in advance!

---

### Post by hyper_ch on 2007-04-02
(1) Once you added the new user you also need to add it to samba (or use an existing user). You can do this by opening the terminal and execute the following command:
```

sudo smbpasswd -a USER

```
After that you can access the share :)

(2) You will have to mount the ntfs drive.

First create where to mount it:
```

sudo mkdir /media/c_drive

```

Second check what the name of that ntfs partition is:
```

sudo fdisk -l

```

This gives for me the following output:
```

hyper@xubi:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        4189     2931862+   5  Extended
/dev/sda3            4190        7836    29294527+  83  Linux
/dev/sda4            7837       60801   425441362+  83  Linux
/dev/sda5            3825        4189     2931831   82  Linux swap / Solaris

```
Then you can see what the ntfs drive is. In my case it's /dev/sda1

Third you mount the ntfs drive with the following command:
```

mount /dev/sda1 /media/c_drive/ -t ntfs -r -o umask=0222

```

Now you have read access to it.

---

### Post by Poogy on 2007-04-02
Man, I can't thank you enough.
Works like a charm!

---

### Post by hyper_ch on 2007-04-02
if you have more problems/questions, just ask :)

---

### Post by Poogy on 2007-04-02
Actually, I do have a general wondering ;-)

Regarding mounting of NTFS disks - assuming I will soon install ubuntu (which seems like what I'll do) - is there any problem with working with these NTFS disks as they are today or is it dangerous for the data on them?
I've noticed that after I mounted the NTFS drive, it was mounted as read-only - is it a best practice not to write to these drives from Linux or is it just a default that I can change?

I'm asking since I have quite a lot of data in my disks and my preferred way was to continue storing the new data (on Linux) on the same folders. IF this is not recommended, I will have to gradually move this data from NTFS disks to ext2 ones.

Thanks again!

---

### Post by hyper_ch on 2007-04-02
Hmmm, there are additional drivers that let you write to ntfs drives but I'd be careful about that. However there are drivers for windows that let windows read/write ext2/3 file systems. That would be, imho, the safer approach...

Or if you don't have any files larger than 2GB you could setup a Fat32 partition to store your data. Neither windoze nor linux have problems with that filesystem.

---

