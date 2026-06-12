---
title: "Mounted NTFS partition only root readable"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by pansz on 2006-09-04
Hello, I know that NTFS is read-only in Linux. However, when I mount NTFS partition in Ubuntu, it is only root readable (mod 500)

I want it to be world readable so that the file manager can read, any work around?

---

### Post by frodon on 2006-09-04
Follow these instructions and you should be good to go : 
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by rohan! on 2006-09-04
> **pansz said:**
> Hello, I know that NTFS is read-only in Linux. However, when I mount NTFS partition in Ubuntu, it is only root readable (mod 500)

I want it to be world readable so that the file manager can read, any work around?

You need to change the options in your /etc/fstab file.
go to terminal and type```
sudo gedit /etc/fstab
``` then find the line that mounts your xp partition and add the word *user* to the option line.

if you don't know what you're doing then you can type *cat /etc/fstab* in the terminal and paste the results here, then it'll be easier to say what to do.

---

### Post by pansz on 2006-09-04
> **frodon said:**
> Follow these instructions and you should be good to go : 
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/DapperGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)
Thanks frodon, from the given link, I'd found that the umask and iocharset options in fstab solves my problem...

To rohan: simply add the 'user' option in fstab does not help in this case, and that is the reason I come here to seek for help   ;-)

---

### Post by kidders on 2006-09-04
Ordinarily when you mount filesystems, the system uses permissions-related metadata on the filesystem itself to help it decide how to represent things. You can override the default behaviour if it doesn't suit you, though.

Take a look in /etc/fstab for a reference to your NTFS partition. Let's say it's at /dev/sda1, for the sake of argument. You probably have something like:

```

/dev/sda1 /mnt/windows ntfs defaults 0 0

```

What I have shown here as "defaults" is a mount options list. I suggest at least using "ro,noexec" here. To solve your problem, you could try adding "uid=0,gid=111,umask=337" to the mix. I'll explain exactly what this means in a moment, but I suggest that you also take a look at the manual page for "mount" for more information ... in particular the section on NTFS mount options.

```

/dev/sda1 /mnt/windows ntfs ro,noexec,uid=0,gid=111,umask=0337 0 0

```

At this point, a note of caution: Please, please be careful with your /etc/fstab. It contains instructions for how to auto-mount things like Ubuntu's root filesystem at startup, and correcting mistakes after the fact pretty much always requires a bootable Linux CD (any Linux will do). **NEVER save any change you don't fully understand!**

**MOUNT OPTIONS DEMYSTEFIED**

The /etc/fstab line above works like this:

[LIST]
[*]**/dev/sda1** - The /dev entry that points to the device you want to mount.
[*]**/mnt/windows** - The mount point. Conventionally, /mnt is a traditional place to put mounted filesystems that don't really belong anywhere in particular.
[*]**ntfs** - The filesystem type. Linux is capable of determining this for itself (use the word "auto"), but there's no point in risking a mis-detection if the partition is fixed (ie not a USB key, etc).
[*]**ro** - Means read-only. NTFS is writable in Linux, but it is not considered "safe" to do so.
[*]**noexec** - Blocks the execution of anything on a given partition ... a good safety precaution for necessarily virus-ridden Windoze partitions.
[*]**uid** - Force anything in the partition to be owned by a particular user ... 0 is "root".
[*]**gid** - Force anything in the partition to be owned by a particular group ... 111 is "admin".
[*]**umask** - A umask is an expression of the file access permissions something DOESN'T have. 0337 gives user & group read-only access and blocks all other access.
[*]**0 0** - These are advanced options related to clean-up.
[/LIST]

So, using the /etc/fstab suggestion above, you can grant users access to your NTFS partition by adding them to the "admin" group on your Ubuntu system.

I hope this helps.

---

