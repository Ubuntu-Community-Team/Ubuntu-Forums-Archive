---
title: "[SOLVED] Unable to change owner: &amp;quot;Operation not permitted&amp;quot;"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by asaz989 on 2007-11-25
I'm trying to change the ownership of a file from "root" to "asa". But every time I try, even with sudo, I get the error message "Operation not permitted".

Here's the command I use: sudo chown asa:asa "College Fees Spring 2008 11-21-07.xls"

All of this is on a separate "files" partition from my root and usr partitions; I don't know if that would be a problem. (this partition is also owned by root, long term I also want to change ownership of the mount directory).

How do I do this? What's going wrong? What exactly is "not permitted" to the root account?

---

### Post by Majorix on 2007-11-25
Try changing the permissions using nautilus in root mode:
```
gksudo nautilus
```

---

### Post by dhughes on 2007-11-25
Maybe try 

```
sudo chown -R asa:asa /home/user/College Fees Spring 2008 11-21-07.xls
```

 since maybe you're not changing everything in the folder (if it is a folder). I see it is an .xls file but who knows maybe you've got it stored somewhere that is messing up what you're trying to do.

---

### Post by bodhi.zazen on 2007-11-25
Is the file on a FAT or NTFS drive ? If so , permissions are not supported on either FAT or NTFS and permissions are set at the time of mount.

---

### Post by asaz989 on 2007-11-25
Thanks, everyone; yeah, it's a FAT drive, and that explains a lot.

Actually, it seems I wasn't quite clear; I HAVE managed to change file *permissions* with sudo; it's just a pain to have to go to the command line for that, and to do it in GUI, it needs to be owned by the logged-in user. Hence the desire to change ownership of the files (and directory), which I *couldn't* do with sudo.

Having said that, if I can't change owner on a FAT partition, is there any other way to change permissions for these files without going to the command line?

Thanks a lot, again.

---

### Post by kvonb on 2007-11-25
-

---

### Post by bodhi.zazen on 2007-11-25
> **asaz989 said:**
> Thanks, everyone; yeah, it's a FAT drive, and that explains a lot.

Actually, it seems I wasn't quite clear; I HAVE managed to change file *permissions* with sudo; it's just a pain to have to go to the command line for that, and to do it in GUI, it needs to be owned by the logged-in user. Hence the desire to change ownership of the files (and directory), which I *couldn't* do with sudo.

Having said that, if I can't change owner on a FAT partition, is there any other way to change permissions for these files without going to the command line?

Thanks a lot, again.

You set permissions and ownership at the time of mount.

mount <device> <mount_point> -o uid=1000,gid=100,umask=007

Or edit /etc/fstab and re-mount.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by bodhi.zazen on 2007-11-25
> **kvonb said:**
> It might be the spaces, use the <TAB> key to autocomplete the name.

When you get to the filename, type the first few letters, then press <TAB>, you will see that it puts a "\" before each space.

You could do that manually, but <TAB> is easier :)

good guess, but we know it is not the spaces because of the use of quotes.

"file with spaces" works as well as file\ with\ spaces

---

### Post by asaz989 on 2007-11-25
Fstabbing worked like a charm (though I did need a bit of a crash course ) Thanks a lot!

---

