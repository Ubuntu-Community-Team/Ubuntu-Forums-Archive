---
title: "[SOLVED] External hard drive (NTFS) permissions"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Belerophon on 2008-02-01
Hi.
I want to make an external usb drive more secure.

So the idea is to give ME all rights over the hard disk, and only READ rights to everyone else...
When I was thinking on how to solve this :), I felt that this is only a matter of common file permissions.
So I thought:
- I must become the owner of everything inside the disk
- use *chmod* to set the permissions recursively over everything inside the disk;

Now, how do I become owner of every file and folder inside that disk??

To set the permissions I want, I must do:
```
chmod 744 <top folder>
```
Is this right??
How to make it recursive to everything inside the drive??
(top folder should be the folder that appears under */media* when I plug the hard drive in, right?)

By the way, if I do all of the above, will everyone still be able to mount the drive??

Another issue, is about windows:
-after I accomplish my objective under Ubuntu, will I be able to use this hard drive under Windows, without problems?? Won't it "reset" all that I may have done before in Ubuntu??

To give a little context on all this, and ask another thing:
I use to make **SSH** connections to a computer that has that hard drive attached; So, I don't want that another user, without administrator privileges, connected by ssh, to write or delete anything inside the hard drive.
I also find it very useful to use **SSHFS** to mount that same external hard drive under the computer I'm making the connection from. 
The question is, if I do all the above(changing permissions...), will I still be able to use the hard drive mounted by **SSHFS** without any problem??

Thanks.
(sorry about the English..)

---

### Post by dannyboy79 on 2008-02-01
it's 
sudo chmod -R 744 /media/
that will make that folder with those permissions but it won't apply any permissions to the NTFS filesystem. that doesn't work in linux. also, I believe when you plug in an external drive it automatically gets mounted unless you setup a udev rule that makes it so that only sudo can mount it but I don't have any experience with that. good luck

---

### Post by Belerophon on 2008-02-01
Are you sure??
So, what can I do to implement file permissions in a NTFS drive???

---

### Post by dannyboy79 on 2008-02-01
here's all the info you could read.
[http://www.linux-ntfs.org/doku.php?id=ntfs-en#what_features_of_ntfs_does_linux_support](http://www.linux-ntfs.org/doku.php?id=ntfs-en#what_features_of_ntfs_does_linux_support)

---

### Post by Belerophon on 2008-02-01
Thanks for the quick reply.
Ok, i read smethings very quickly...I'll decide later what to do...if keep the ntfs, or format the drive to EXT3...


But suppose I turn the drive to EXT3, can someone help me with my original questions??

Thanks.

---

### Post by dannyboy79 on 2008-02-01
certainly. this would still work, only certain people would have access to the /media/ folder. it's just that the permissions are set for that folder and not for each NTFS filesystem file. that should work making the /media/ 744. but anything that gets mounted there would have those permissions.

---

### Post by Belerophon on 2008-02-01
> **dannyboy79 said:**
> certainly. this would still work, only certain people would have access to the /media/ folder. it's just that the permissions are set for that folder and not for each NTFS filesystem file. that should work making the /media/ 744. but anything that gets mounted there would have those permissions.

Ok, I'm not sure if I understood what you meant...but let's go:
-if I keep the drive formated in NTFS, and apply the 744 permissions to the top folder, what you say is that the permissions are only applied to the top folder?
-How would applying the permissions to the /media folder help me?? I didn't understand this...

But what about if I turned the drive into EXT3?...

Thanks

---

### Post by dannyboy79 on 2008-02-01
> **Belerophon said:**
> Ok, I'm not sure if I understood what you meant...but let's go:
-if I keep the drive formated in NTFS, and apply the 744 permissions to the top folder, what you say is that the permissions are only applied to the top folder?
-How would applying the permissions to the /media folder help me?? I didn't understand this...

But what about if I turned the drive into EXT3?...

Thanks

if you make the folder where you mount your ntfs drive 744, then it will be readable/writable/executable by the owner, readable only for the group and others. the /media/ folder is a mount place for whatever you mount there and will keep those permissions/owner/group settings. you just can''t apply chmod or chown to folders that are on a NTFS filesystem. actually I just re-read that link, it does say that you can mount it with umask and apply certain permissions that way. see, there's permissions for folders, then there's permissions on how the drive was mounted. so if the folder has read/write/execute for only the owner, but you mount it using special permissions, it wouldn't matter because the folder is already set. see what I am saying? so you would want to leave the /media/ folder the way it is because other usb sticks and whatnot get automounted there, just use the umask option when you mount the drive to control who can write to it. I am not sure about SSHFS.

---

### Post by Belerophon on 2008-02-01
Yes, it was never my intention to apply any type of permissions to the /media folder...
I read that thing about umask too, that's why I'll decide later if I use that kind of thing to the NTFS file system, or just reformat the disk to EXT3...

What is *chown*?

Thanks very much for the help!

Still I'd like to see some feedback on the SSHFS question...

---

### Post by dannyboy79 on 2008-02-01
chown is what you use to change the owner/group of folders and files.

sudo chown daniel:daniel /media/

would make the media folder owned by user daniel and group daniel. you can most of the time read all about commands in the man pages within linux. just enter this in the terminal to find out about something that someone is telling you. it'll help you learn faster as well.

man chown

---

### Post by Belerophon on 2008-02-01
Hummmm ;) will do...thanks

---

### Post by bodhi.zazen on 2008-02-01
Just a FYI, NTFS does not support permissions or ownership, and neither chown or chmod will work on a FAT or NTFS partition.

You set permissions at the time of mount with options, uid=xxx, gid=yyy, umask=zzz

Or with ntfs-config : ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

For additional information see : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Belerophon on 2008-02-02
ntfs-config is just to enable or disable writing in NTFS partitions, not to set permissions...!!....right?

---

### Post by bodhi.zazen on 2008-02-02
> **Belerophon said:**
> ntfs-config is just to enable or disable writing in NTFS partitions, not to set permissions...!!....right?

Yes, that is correct, but I threw it out there as enabling write permissions is the most common permission people want with their ntfs partitions.

---

### Post by Belerophon on 2008-02-03
Well, I've decided to format the drive in EXT3...

The permissions work perfectly, and now I have my drive protected from other users like I wanted...

All works perfectly when I mount the drive through sshfs...

Now I have to see what will happen when I connect the drive in Windows, after installing something to work with EXT3 ;)....don't know if I'll be able to write there..

Thanks!

---

### Post by bodhi.zazen on 2008-02-03
> **Belerophon said:**
> Well, I've decided to format the drive in EXT3...

The permissions work perfectly, and now I have my drive protected from other users like I wanted...

All works perfectly when I mount the drive through sshfs...

Now I have to see what will happen when I connect the drive in Windows, after installing something to work with EXT3 ;)....don't know if I'll be able to write there..

Thanks!

Install the fs-driver :

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

---

