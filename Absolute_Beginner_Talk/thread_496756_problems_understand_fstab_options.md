---
title: "problems understand fstab options"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-07-09
I'm using Feisty on an HP Pavilion dv8000 notebook.

I've been hacking at fstab for a couple days now and I'm still unsure about a couple things. I'm hoping there is someone who really understands how to set up fstab to mount external filesystems.

I'm presently trying to set up my neighbor's laptop. It has two hard drives. I've put a copy of xp on the first drive and I've set up the second one for Linux with Gparted. I'll throw my partition tables in here for the heck of it(using fdisk -l).
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   5  Extended
/dev/sdb2            8925        9729     6466162+  83  Linux
/dev/sdb5               1          13      104359+  83  Linux
/dev/sdb6              14         140     1020096   82  Linux swap / Solaris
/dev/sdb7             141        1415    10241406   83  Linux
/dev/sdb8            1416        8924    60316011   83  Linux

```

The only partitions outside of Linux is sda1, which holds Windows, and sdb2, which is just an extra partition. I'm more concerned with being able to read and write to Windows, but it seems I'm having the same problems with sdb2 as well. I'll now show what I've done to my fstab.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=9b71fc43-1795-445d-a9cf-30ac875cc9c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=abfa736d-84a2-46f4-9ced-779614dbf114 /boot           ext3    defaults        0       2
# /dev/sdb8
UUID=5978921b-4818-40a2-94ee-67cf52a042e9 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D8BCDF4EBCDF2632 /mnt/Windows     ntfs    user,rw,sync,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=5a44152e-8ce6-4b3b-9148-23746ca49667 /mnt/sdb2     ext3    user,rw,sync        0       2
# /dev/sdb6
UUID=be77f257-0b3d-4ed9-9671-178fcfcfbf50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is what it shows when I use **mount**.
```

/dev/sda1 on /mnt/Windows type ntfs (rw,noexec,nosuid,nodev,sync,nls=utf8,umask=007,gid=46)
/dev/sdb2 on /mnt/sdb2 type ext3 (rw,noexec,nosuid,nodev,sync)

```

Does everything look okay? Do I just need to change the folder permissions to these filesystems? Isn't there a way to make the directory the filesystem is mounted to accessable to all users? I've been reading how-to after how-to and I guess I just don't understand all of it. I've never really dealt with file permissions before.

Also, I've been reading that you need to download a certain driver to be able to access an ntfs filesystem. Is this so?

If anyone could throw some suggestions at me, that would be great. Thank you.

---

### Post by Omnios on 2007-07-09
You might find this link useful.

its about fstab entries.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Pragmatist on 2007-07-09
You could make it accessible to yourself by using the uid parameter. uid just stands for "user ID".  Typically, your uid will be 1000  Type this to find out your uid:
```
id
```You would change your fstab line accordingly (i.e. change the uid from 46 to 1000)

If you want to make it accessible to other users (are you sure you want to do that!) you use the umask variable.  Right now your umask is set to 007

A brief explanation of permissions:
Permissions fall into three categories, the **owner**, the **group**, and **others**.  In order to see permissions for any file, you can use the ls command with -l switch:
```
ls -l
```You will see something like:
> -rw-r----- 1 root adm 142850 2007-07-09 10:38 /var/log/messagesThere are 10 positions, but we are only going to consider 9 of them.  Ignore the first place (each place is designated by a - ).  r stands for read and w stands for write and x stands for execute.  The most permissions would be this:

-rwxrwxrwx

The first three permissions refer to the owner of the file, the next three to the group owners of the file, and the final three to everybody else (others). For the previous file, everybody can do everything.

Numbers are also used, rather than letters.  r=4 w=2 x=1  To include all the permissions you would have 4+2+1=7  So the above permissions is 777 For the previous file: 

-rw-r-----

would be 4+2+0=6  and 4+0+0=4 and 0+0+0=0  So the permissions are 640

Finally, we come to umask  umask is the inverse of the above numbers.  So 777 becomes 000 and 640 becomes 7-6 + 7-4 + 7-0  or  137

So what does your umask of 007 mean?  You just subtract the umask from 777 so:

777
-
007

770 or rwxrwx---

This means that any file created on that mounted file system will by default have permissions of 770 or rwxrwx---

On my main system my umask is 133 (which means 644 permissions)and for my external usb drive it is 077 (700 permissions).  One way to check is to just make an empty file:
```
touch testfile
```Now check the permissions:
```
ls -l testfile
```You can change the ownership using the **chown** command and the permissions using the **chmod **command.  Read the man pages to know more about them.

---

### Post by steve.horsley on 2007-07-09
On NTFS, it can't store permissions flags so the permissions are emulated, defined by the mount command, and they apply to every file on the partition. A umask=0 says to emulate all permissions for all users (see Pragmatits's post for details).

For the ext3 partition, it can store unix permissions, so it's just a matter of assigning the appropriate permissions, usinf **chown** to change owner and **chmod** to change permissions flags. Actually, it's probablu easier to use this command:
**gksu nautilus**
to launch a file explorer with admin privileges, and then right-click files/folders and set their permissions in the GUI. It is worth getting familiar with permissions, and how to chang them on the command line - you mak need that skill one day.

---

### Post by Inxsible on 2007-07-09
Here's another great link to [understand fstab]("http://doc.gwos.org/index.php/Understanding_fstab")

To make mounted drives accessible to all users, you need to put in a "users" option in the fstab entry. (without the quotes of course). Go thru the link I gave you, it details fstab very nicely.

---

### Post by Inxsible on 2007-07-09
You will need ntfs-3g to write to an ntfs filesystem. Reading doesnt require any special drivers.

you can install ntfs-3g by Applications-->Add/Remove. Search for "ntfs" with out quotes.

Install NTFS Configuration Tool. After installation, Go to Applications-->System Tools--> NTFS Configuration Tool and enable write support for internal as well as external drives.

---

### Post by clinto on 2007-07-09
@Pragmatist
That was ****ing awesome! i didn't know any of that about the permission codes. Thank you very much for your time and knowledge!

Everyone else as well. Thank you.

There's one thing I forgot to note. I've noticed that when you change the permission on a directory, it doesn't apply the same permissions to the files and directories under it. Is there a way to change all the permissions under one directory with a single command?

If I've missed the answer to this in one of your posts or if it's pretty obvious, I apologize.

---

### Post by bodhi.zazen on 2007-07-09
Management of permissions is different for windows (fat/ntfs) partitions then linux partitions.

See Inxsible 's lilnk for full information.

To answer your question, use the -R flag

sudo chmod -R 777 /directory

See [man chmod](http://linux.die.net/man/1/chmod) for further information .

> -R, --recursive
    change files and directories recursively

---

