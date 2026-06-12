---
title: "Problems with premission changes"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by pcorajr on 2006-02-26
I am having problems seeting up a permission schema on a share i have running on my ubuntu. 

The files are on a partition of their own and here is how the directory branch off

hdb1
|
backups
|
17 folders (APPZ,MP3,Movies,ect.....)
|
More folders and file withing the above mention files.

So for example the MP3 folder has mp3 files and 3 sub-folders that have more Mp3.

 

the problems that I am having is that i want to make every directory in the partition have 755 permissions and I want every file to have 644 permissions.

but I dont know how to achive this 

I have used every switch  on chmod to achive what i want but no luck yet. I have tried the following  

chmod -R 755 {DIRECTORY} 

AND 

chmod -R 755 *.*

I am wondering if there is a script or mix of commands that could help me do this with out having to go to each directory and file and change the permissions. one thing to note is that this is not the full list of directorys I have there is more but I just wanted to give an idea of the layout. Also these directorys and files are part of my SMB file system and FTP server content. So these files are been access from a windows box and also a few friends an relatives access them thru FTP. So evetually my goals are to create users and  group and apply them to the permissions or vice versa.

thanks in advace 

*[SIZE="7"]P[/SIZE]cora[SIZE="7"]J[/SIZE]R*

---

### Post by vbmaster on 2006-02-26
Well, thats a difficult setting to make automatically, but I can help a bit, however, i can't solve your problem totally.

If you want some king of permissions in a separate partition you'll only have to edit the /etc/fstab and in the correct partitions set de umask value.

The umask é similar to chmod, but the inverse, i mean, if you have a 7 chmod permission it'll be a 0 umask permission, because de umask gives us the value that lacks to reach 7. Another exemple, if you want a 4 chmod permission it'll be a 3 umask permission.

So if you want a 644 permissions schema you only have to set the umask in festab to umask=133.

But that will aply the setting to all the files.... ;)

---

### Post by Sutekh on 2006-02-26
Actually thats a good suggestion **vbmaster**.  

**pcorajr** you say that this is a share partition that is used by Windows?  So can I assume that it is formatted FAT32?

If so you should look at your /etc/fstab and determine how the partition is mounted.  

Instead of using **umask** you could use **fmask** and **dmask**.  They work in a similar way to **umask** except that they control permissions for the files and directories respectively.

If you want 755 permissions for directories use **dmask=0022**

If you want 644 permissions for files use **fmask=0133**


For the future when you want to alow certain users and groups access to the files, you can include the flags **uid** - user id number, and **gid** - group id number, to the /etc/fstab entry.

Check out the man page for mount for some more explanationon umask, dmask, fmask, uid and gid. 

[mount (8) inux Man Page]("http://www.die.net/doc/linux/man/man8/mount.8.html")

---

### Post by denday on 2006-08-12
thanks for advice, now I can manage my hda totaly: 

drwxr-xr-x 2 root root  4096 Aug 10 04:40 cdrom0
drwx--x--x 1 root root  4096 Aug  9 19:41 hda1
drwx--x--x 1 root root 12288 Aug  8 15:58 hda5
drwx--x--x 1 root root  4096 Aug  8 15:58 hda6
drwx--x--x 1 root root 12288 Aug  8 15:58 hda7

---

