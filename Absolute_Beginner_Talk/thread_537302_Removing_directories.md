---
title: "Removing directories"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by AlastairGrant on 2007-08-28
Ok i've not used linux for a while... but trying to remove a directory which is not empty.

Is there a way I can do it easily  (rmdir doesn't seem to have an option to remove non-empty directories).

Ideally, I would like to be able to do it from the 'File Browser' app?

Also is there a way I can log on as root rather than just in the Terminal window?

Thanks, Alastair

---

### Post by dwhitney67 on 2007-08-28
This will remove a directory and its contents with extreme prejudice:

[FONT="Courier New"]$ rm -rf <dir>[/FONT]

Of course you must have permission to do so.  If you do not, and you are confident in what you are doing, precede the command with "sudo".

It is never a wise idea to log into the root account from the GDM login, but on most Unix systems it is doable.  But I am not sure about Ubuntu.

Have you set the root password to something other than the system default?  I bet most Ubuntu users have not.

P.S.  From a File Browser, you can move a directory to the trash if you want to delete it (and its contents).

---

### Post by Caffeine_Junky on 2007-08-28
Here is a link I keep bookmarked & in my sig,  ..comes in handy some times  :P

[[COLOR="Blue"]Manipulating Directories in linux[/COLOR]]("http://www.tuxfiles.org/linuxhelp/dirman.html")

cheers

---

### Post by dwhitney67 on 2007-08-28
> **Caffeine_Junky said:**
> Here is a link I keep bookmarked & in my sig,  ..comes in handy some times  :P

[[COLOR="Blue"]Manipulating Directories in linux[/COLOR]]("http://www.tuxfiles.org/linuxhelp/dirman.html")

cheers

Nice little guide.  I would recommend that in lieu of "cp -r dir1 dir2" for copying directories, that the '-r 'be replaced with a '-a', so as to preserve time-stamps and symlinks of the dir1 directory.  The '-a' option implies the '-r' as well.

---

