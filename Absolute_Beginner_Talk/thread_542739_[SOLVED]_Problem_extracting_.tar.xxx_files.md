---
title: "[SOLVED] Problem extracting .tar.xxx files"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by apparle on 2007-09-04
Wherenever I extract any .tar.xxx file receive command line error though the files get extracted.

The error is
 
"Cannot utime :  Operation not permitted"

Using Feisty Fawn 7.04 i386

I also extracted the same file in Windows(dual boot) without any error.
Then I compared some of the WIN extracted files and files extracted with error in ubuntu
by md5 check sum they matched??????????????
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by ryanVickers on 2007-09-04
are you possibly trying to extract to a read-only folder, or you don't have permissions?  Try moving the archive to your desktop and then do a "Extract here".  It *should* work...

---

### Post by apparle on 2007-09-04
I am not using readonly folder and I have permissions to create and delete files.
When I boot from 32bit live CD it extracts fine

I also told you it creates the files which have matching md5 sum

---

### Post by ryanVickers on 2007-09-05
wierd. it's not just *one* archive that's a problem is it?

---

### Post by apparle on 2007-09-06
But what is the solution.
The problem is with only tar files

---

### Post by steve.horsley on 2007-09-06
> **apparle said:**
> But what is the solution.
The problem is with only tar files

You could try using **tar -m**. 

What filesystem are you extracting on? I wonder if it's an odd filesystem that doesn't allow setting the modification time of the extracted files.

---

### Post by hyper_ch on 2007-09-06
what permissions does the .tar.gz file have?

---

### Post by ryanVickers on 2007-09-06
> **apparle said:**
> But what is the solution.
The problem is with only tar files

to be honest, at this point, I'm kinda lost now, but other people seem to have found your post, so I'll leave now :)

---

### Post by apparle on 2007-09-07
Ok guys problem solved.
The extraction was problematic only on fat32 system
When i moved the file to ex3 system it worked fine.
Thanks for the help guys

---

### Post by jalanbuntu on 2007-09-24
> **apparle said:**
> Ok guys problem solved.
The extraction was problematic only on fat32 system
When i moved the file to ex3 system it worked fine.
Thanks for the help guys

Are you sure thats because the fat32 problem?
I got the same problem here. When I try to extract from the mounted fat32
partition, I got the _utime permission denied error_
I'm not so sure that because the fat32 partition, but the file permission, I guess.
I also can't change the permission to 777, even if I'm changing it from root account.

Below is my fstab configuration..
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c1885f42-97fa-495b-904d-9f7a93eacb24 /               reiserfs notail          0       1
# /dev/sda5
UUID=45FE-4A35  /media/sda5     vfat    defaults,utf8,umask=007,gid=1000 0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/swap.swp       none            swap    sw      0       0
```


Maybe there are something incorrect with my fstab setting?

---

### Post by apparle on 2007-09-27
Hey I am a begineer and don't understand any thing .
But one thing for sure 
Copy the archive to your deskop and then extract
I was getting the same error and I copied the file to my desktop it worked

---

