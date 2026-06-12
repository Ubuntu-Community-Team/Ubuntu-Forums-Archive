---
title: "How to: Mount FAT32 Partition with FULL permissions"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by mezer on 2007-01-07
Hello!  

This is my first post, as i just switched over to UBUNTU yesturday

I have a FAT32 partition that holds all my MP3's.  I have it automounted using the fstab file.  Here's the entry 

"/dev/sda2 /home/mezer/Desktop/Stuff     vfat  umask=0,dmask=0000,uid=501,gid=users,users  0 0"

I can't edit the TAGS of the mp3 files because i don't have write privs to the files.  It says the OWNER of these files are "501" and they are read only

Notice the LOCK on the files (pic: "http://i26.photobucket.com/albums/c135/mezer/Misc/lockedmp3.jpg")

How do i get full privledges to this FAT32 partition so i can edit the files on it while having it mounted?

Thanks

---

### Post by taurus on 2007-01-07
I would replace the **gid=501** to the actual group you belong to.  I am sure it's 1000 but you can find out for sure with this command from a terminal.

```
id
```

---

### Post by mezer on 2007-01-07
One step closer.  I am using

"/dev/sda2 /home/mezer/Desktop/Stuff vfat umask=0,dmask=0000,uid=1000,gid=users,users 0 0"

And now when i view the mounted volume, it says that I am the owner of these files.  

PROBLEM is, they are in read only.  

What command should i add to the above mount line to make it read / write?

Thanks

---

### Post by Koybe on 2007-01-07
Try to add 'rw'

"/dev/sda2 /home/mezer/Desktop/Stuff vfat rw,umask=0,dmask=0000,uid=1000,gid=users,users 0 0"

---

### Post by taurus on 2007-01-07
Why don't you mount it somewhere else like this (in /etc/fstab).

```

/dev/sda2   /media/Stuff   vfat   iocharset=utf8,umask=000   0   0

```
Then, unmount it and remount it to a new mount point.

```
sudo mkdir /media/Stuff
sudo umount /dev/sda2
sudo mount -a
```

---

### Post by mezer on 2007-01-07
> **Koybe said:**
> Try to add 'rw'

"/dev/sda2 /home/mezer/Desktop/Stuff vfat rw,umask=0,dmask=0000,uid=1000,gid=users,users 0 0"

Just tried this and same problem.  Mounted as read only.

**NOTE**: The folders are ALL read/write.  But the files are read only

---

### Post by Omnios on 2007-01-07
Hi I have been using a vfat document drive for both windows and Linux documents and found this set up about a year ago and have been using it ever since.

```

/dev/hda2       /media/documents     vfat rw,users,gid=users,umask=000,       0       0

```

/dev/hda2 = the partition being mounted. /media/documents = the mount point to a directory in media.

 As a note the mount directory will be the name of the partition in gnome.


 I also have a good vfat link in my signature.

---

### Post by Koybe on 2007-01-07
And what does 'mount' show as an output?

---

### Post by mezer on 2007-01-07
> **Koybe said:**
> And what does 'mount' show as an output?

/dev/sda2 on /media/Stuff type vfat (rw,iocharset=utf8,umask=000)

---

### Post by mezer on 2007-01-07
This is the closest i can get

The FOLDERS are all owned by me, and permission is RW.  But the files inside the folders are only R.

Using this line in fstab -

 /dev/sda2       /media/Stuff     vfat rw,users,uid=1000,gid=1000,umask=000,       0       0

Mount shows - 

/dev/sda2 on /media/Stuff type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=000)


*** Any Ideas?

---

### Post by mezer on 2007-01-07
I can delete files... and rename files..., but just can't edit them

Is there another line i should add to fstab?  Or another command?

---

### Post by Ocxic on 2007-01-07
get rid of the uid, and gid in the fstab line.
then "sudo chown -r your_username:your_username /mount/point"
sould do the trick. it make you the owner of the folder, and everything in it.

---

### Post by mezer on 2007-01-07
Does the "sudo chown -r........" go in the fstab?  Inplace of the UID and GID?

I'm trying to make this auto mount

---

### Post by mezer on 2007-01-07
I removed the above from the fstab.. remounted.. ran your code and it came back as invalid, -r isn't valid.

---

### Post by mezer on 2007-01-07
I did -hR instead of -r, i also just removed the switch

I get "Operation not permitted"

This was done on ROOT and my account

ANYONE ELSE? PLEASE!

---

### Post by Koybe on 2007-01-08
chown -R youraccount: /path/to/your/mountpoint

---

### Post by mezer on 2007-01-08
CHOWN is a command that changes ownership.  I've already stated that i have the ownership.. but it's read only on files, and read and write on folders. 

That doesn't help when i'm trying to edit a file within a subfolder

Been doing some research at work, i'm going to try CHMOD -R 777 /folder.

I think that will change permissions to read/write on ALL contents inside the folder.. subdir's also

Since this is a FAT32 volume, i'm not sure if CHMOD will work on it, so i'll copy the MP3 files to my ext3 partition, change permissions, then copy back to fat32

---

### Post by Koybe on 2007-01-08
777 means allowing everything to everyone. And make all files executable. Maybe you can just add the permission you need. 

chmod -R g+w /folder will add write permission to all files and subfolders for the proprietary group.

Then you can set what you want with this :
u=user
g=group
o=others

r=read
w=write
x=execute

Just change according your needs.

---

### Post by mezer on 2007-01-08
Thanks, i'll give that a shot when i get home from work.

---

### Post by mezer on 2007-01-08
I can now change permissions of files in subdirectories.

But when i copy these files back onto the fat32 volume i have mounted.  It's read only

*** How can i mount this FAT32 volume in read and write for FOLDERS, SUBFOLDERS, & FILES ***

Does nobody else have this problem?

---

### Post by mezer on 2007-01-08
Nevermind..

I'm going to get rid of this fat partition and format it as ext3.  I'm sure i'll have less problems with permissions and such after that

Thanks

---

### Post by jomon_johnson on 2007-01-08
First u login as root by " su - ". Then unmount mnt if mounted by " umount  /mnt "
then mount as " mount -t vfat /dev/hdaX /mnt " where ' X ' is a number representing corresponding partition.most commonly hda1 is  c: 
Thanks

---

### Post by jhp-dk on 2007-02-02
It worked for me... thank you so much...  :D

---

