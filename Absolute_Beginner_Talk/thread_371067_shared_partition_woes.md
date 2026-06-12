---
title: "shared partition woes"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by livinjean on 2007-02-26
Hi all,
 I have a total newbie question for you guys.
 "why do all files created  from WinXP on my shared partition (FAT32) show up as executables in Ubuntu?"

 this becomes particularly annoying when trying open a text file, because gedit asks me what to do with the file 'run in terminal or open...etc.'

initial research on this issue informs me that this might be a file permissions & mount issue. My current fstab entry for the FAT32 partition is this
```
/dev/sda4 /media/DATA vfat iocharset=utf8,umask=000 0 0
```

any ideas to solve this issue OR links to threads with similar issue 
will be greatly appreciated.

thanks.

---

### Post by bodhi.zazen on 2007-02-26
The problem, as you know, is FAT does not have permissions.

You can see man mount for options ...

[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

Specifically, try > dmask=value
    Set the umask applied to directories only. The default is the umask of the current process. The value is given in octal. 
fmask=value
    Set the umask applied to regular files only. The default is the umask of the current process. The value is given in octal.

Thus, rather then umask=000

Try dmask=000,fmask=111

And re-mount

---

### Post by igknighted on 2007-02-26
2 things... ntfs-3g was released a few days ago as a final release, it is out of beta, so this might be an option for you.  I would still recommend using ext3 as you shared partition though.  It is the most stable partition of all of the options, and has the best read/write support in linux and windows.

---

### Post by livinjean on 2007-02-26
thanks for the reponse, will update you guys after trying these suggestions once I get back home to my laptop :)

---

### Post by livinjean on 2007-02-26
> **bodhi.zazen said:**
> The problem, as you know, is FAT does not have permissions.

You can see man mount for options ...

[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

Specifically, try 

Thus, rather then umask=000

Try dmask=000,fmask=111

And re-mount

bodhi, this idea doesn't seem to work, after making the suggested changes the files created on the FAT32 partition from linux were also being assigned as executables.

> 2 things... ntfs-3g was released a few days ago as a final release, it is out of beta, so this might be an option for you. I would still recommend using ext3 as you shared partition though. It is the most stable partition of all of the options, and has the best read/write support in linux and windows.
igknighted can you suggest me the best way to have read/write access to a ext3 partition from windows (maximum access rights, compatibility with naming conventions for files, auto-mount of ext3 partition at windows startup etc.)

I also noticed something weird, I was in winXP and put my system to hibernate, then booted in linux and created a file in FAT32 shared partition, when I booted in winXP again this new file was not visible, I could access it only after the complete restart of winXP; what could be the possible reasons for this ?

---

### Post by bodhi.zazen on 2007-02-26
Well, I guess I do not know the problem then.

It could be two things.

Setting the permissions of OLD files at mount time should be handled by the options in fstab (mount).

Setting permissions of NEW files as you create them is a different, but similar problem.

Both are handeled with umask.

[http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255](http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255)

---

### Post by livinjean on 2007-02-26
> **bodhi.zazen said:**
> Well, I guess I do not know the problem then.

It could be two things.

Setting the permissions of OLD files at mount time should be handled by the options in fstab (mount).

Setting permissions of NEW files as you create them is a different, but similar problem.

Both are handeled with umask.

[http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255](http://www.linuxsecurity.com/index2.php?option=com_content&do_pdf=1&id=117255)

the issue is "Ubuntu should not ask me everytime that I want to open file in a terminal or display its contents"

from what you have told me, I think I need to figure out the umask value which will allow only read/write but not executable permissions for the files. 
Anyway, I am only planning to keep pictures,movies,songs,documents, firefox/thunderbird profiles etc. in this shared FAT32 partition i.e. none of the data in this partition needs to be executable. (but if you can think of a scenario where it has to be executable to be successfully shared between winXP & linux, please let me know)

---

### Post by bodhi.zazen on 2007-02-26
LOL 

At any rate, for those windows ext3 drivers you were asking about :

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

