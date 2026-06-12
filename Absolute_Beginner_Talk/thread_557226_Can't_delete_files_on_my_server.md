---
title: "Can't delete files on my server"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-22
Hi I have started to use a server to store my files. But i can't really get it to work properly. The setup is:

Ubuntu server with a shared folder /home/rudolf where there is a music folder
Then I have another harddisk formatted NTFS (because i want to acces files from my windows laptop). This drive is mounted in fstab with
> # Backup
/dev/hdb1 /media/Backup_200GB ntfs-3g defaults 0 0
# Medier
/dev/hdb1 /media/Medier_100GB ntfs-3g defaults 0 0

Then I have a symlink for both of those drives in /home/rudolf which is shared on the network.

But the problem starts when I try to create a folder and a file within that folder. If I want to delete that again, it won't let me delete the folder. I can delete the file but when i try to delete the folder i get the message that says that I can't delete it because it is not on same filesystem.

The wired thing is when I then try to delete it from the servers terminal with:
> sudo rm -r /home/rudolf/Backup_200GB/folder
or
> sudo rmdir /home/rudolf/Backup_200GB/folder
It says that I can't delete it because: File exist

If i reboot and try again from terminal there is no problem to delete it.

What am I doing wrong? I guess I'm mounting it wrongly but I don't know any other method

---

### Post by Pumalite on 2007-09-22
Backup your /etc/fstab first, then change this:

 # Backup
/dev/hdb1 /media/Backup_200GB ntfs-3g defaults 0 0
# Medier
/dev/hdb1 /media/Medier_100GB ntfs-3g defaults 0 0
 To this:

 # Backup
/dev/hdb1 /media/Backup_200GB ntfs-3g rw defaults 0 0
# Medier
/dev/hdb1 /media/Medier_100GB ntfs-3g rw defaults 0 0

Reboot and let's see what happens.

---

