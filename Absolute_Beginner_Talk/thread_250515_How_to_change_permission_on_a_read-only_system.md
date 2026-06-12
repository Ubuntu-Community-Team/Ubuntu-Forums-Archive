---
title: "How to change permission on a read-only system"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-09-04
Hello.

Im trying to find out how i can change the permission to my /media/hdd1 hard drive, but all i get is:

chown: changing ownership of `/media/hdd1/': Read-only file system

but nothing happens ](*,) how can i make this system a "non" read-only system so i can change this?

Im realy new to ubuntu/linux but i have manage to do alot in those 2 weeks iv used it, most of it from searching and reading on the net. But now its gone to an hold here](*,) 

So please help me :roll:

---

### Post by cocteau on 2006-09-04
what filesystem is on there?

Generelly all mount options are specified in /etc/fstab. You can set the mount option with a umask=0755. That will allow the owner to read, write and execute on the filesystem.

---

### Post by cantormath on 2006-09-04
> **U5tabil said:**
> Hello.

Im trying to find out how i can change the permission to my /media/hdd1 hard drive, but all i get is:

chown: changing ownership of `/media/hdd1/': Read-only file system

but nothing happens ](*,) how can i make this system a "non" read-only system so i can change this?

Im realy new to ubuntu/linux but i have manage to do alot in those 2 weeks iv used it, most of it from searching and reading on the net. But now its gone to an hold here](*,) 

So please help me :roll:

what are you trying to do?

---

### Post by U5tabil on 2006-09-04
Well when i instaled the ubuntu it set the other hard-drive to /media so i didnt change anything. And since the hard-drive is full of stuff that i have colected over the years when i used WinXP, most videos and mp3s.

What im trying to do was that i wanted to move some files that iv downloaded here to my hard-drive but that didnt work because of the permisson, and then i think there is something to do with the read-only system, that i need to change or something and then change the permission for my user to move/copy files/folder over to that hard-drive without use of commands. But now it doesnt even work in commands becasue of the read-only.

Im frustraited and its hard to explain right now.

---

### Post by cantormath on 2006-09-04
if that drive was your old windows drive, like you save stuff and partitioned the drive from windows, you will need ntfs-3g to read/write to that drive without reformating it.  If you dont use ntfs-3g, you will only have read capability because windows/M$ sucks, and because the drive is formated NTFS.

[a howto]("http://ubuntuos.wordpress.com/2006a/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/")

---

### Post by U5tabil on 2006-09-04
> **cocteau said:**
> what filesystem is on there?

Generelly all mount options are specified in /etc/fstab. You can set the mount option with a umask=0755. That will allow the owner to read, write and execute on the filesystem.


iv tryed that but it didnt work :-k nothing happend. i even ctrl+alt+backspace

---

### Post by cantormath on 2006-09-04
> **U5tabil said:**
> iv tryed that but it didnt work :-k nothing happend. i even ctrl+alt+backspace

well that does nothing, ctl+alt+backspace will restart the xserver(your gui interface).  you need to, like howto says, add install fuse and ntfs-3g and whatever else its says, and then add the mount using ntfs-3g to fstab file, make a mount point, put fuse in the list of mods to load and reboot.

its all in the howto, 

If that does not work for you, im not sure what you can do.
Are you dual booting?

---

### Post by U5tabil on 2006-09-04
> **cantormath said:**
> well that does nothing, ctl+alt+backspace will restart the xserver(your gui interface).  you need to, like howto says, add install fuse and ntfs-3g and whatever else its says, and then add the mount using ntfs-3g to fstab file, make a mount point, put fuse in the list of mods to load and reboot.

its all in the howto, 

If that does not work for you, im not sure what you can do.
Are you dual booting?

Iv read the Dapper guide about mounting. But it says:

mount: /dev/hdd1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hdd1 is mounted on /media/hdd1

so i need either to unmount it and then mount it againg. or else i dont know...

sorry did something wrong but when i now do i get:

u5@U5tabil:~$ sudo mount /media/hdd1/ /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: /media/hdd1/ is not a block device

what the ..... ](*,)

---

