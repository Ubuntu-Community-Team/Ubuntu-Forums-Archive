---
title: "Gaining permission to a mounted drive"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by scratched on 2006-03-25
I mounted my windows NTFS partition to /media/windows, and when I try to open it to browse my files, I get an error that says "You do not have the permissions neccessary to view the contents of 'windows'."

What do I need to do to get those permissions?

I checked the properties of windows and at the bottom of the dialogue it says "You are not the owner, so you can't change these permissions"

---

### Post by Mustard on 2006-03-25
Have a read over these instructions and see if you have any questions about them...

[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

The above link will show you the options you need to add to mount the drive with permissions to read it.  With NTFS you can't write to them anyway from linux, so it will be read only.

---

### Post by Magrioteli on 2006-03-25
Look at this thread, which I started and its answer solved all my quetions 

[http://ubuntuforums.org/showthread.php?t=149338](http://ubuntuforums.org/showthread.php?t=149338)

---

### Post by scratched on 2006-03-25
Thanks, that worked. I knew I couldn't write to NTFS partitions, but I wanted to at least be able to open my files from windows.

---

### Post by Magrioteli on 2006-03-25
[QUOTE=scratched]Thanks, that worked. I knew I couldn't write to NTFS partitions, but I wanted to at least be able to open my files from windows.[/QUOTE]

Good that it worked. 
We're lucky so far, reading that NTFS-stuff! ;)

---

