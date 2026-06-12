---
title: "Paths and $PATH"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-20
Could someone tell me the meaning of this: ```
 buck@argos:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory
buck@argos:~$
```

The above list of directories is the default, and they all exist.  If I add directories to the $PATH, the "No such file or directory" warning is always at the end of the list.  While I'm asking, is there a configuration file somewhere that sets these paths?

Thanks,
Buck

---

### Post by po0f on 2006-12-20
Buck2348,

The best place to set your PATH is in ~/.bashrc.  Something like the following should work:
```
[FONT="Courier New"]PATH="/my/bin/path:$PATH"[/FONT]
```
After doing that, you can `source ~/.bashrc` or just close any open terminals and fire up a new one.  `echo $PATH` to confirm that the changes took place.

---

### Post by GuitarFingers on 2006-12-20
To update the Path variable for the current session and add a new path to it use the following command:

PATH=$PATH:/path/tonew/directory

Notice there's no "$" in front of the first path and don't forget the ":" before the new path, that separates it from the previous path in the list and will save you getting the "Path Not Found" error.

To permanently set the path add a line to your .bash_profile file that you will find in your home directory with that command in it.

Hope that helps,
GuitarFingers

---

### Post by pandu.rs on 2006-12-20
if ur intention was to view the contents of variable PATH then u shld use

echo $PATH

---

### Post by Buck2348 on 2006-12-21
> **pandu.rs said:**
> if ur intention was to view the contents of variable PATH then u shld use

echo $PATH
Thanks, pandu.rs--I realized that first thing today when I looked at it.  I'd stil like to know just why my mistaken command gives the paths but with the "no such file or directory" error.

> **GuitarFingers said:**
> To update the Path variable for the current session and add a new path to it use the following command:

PATH=$PATH:/path/tonew/directory

Notice there's no "$" in front of the first path and don't forget the ":" before the new path, that separates it from the previous path in the list and will save you getting the "Path Not Found" error.

To permanently set the path add a line to your .bash_profile file that you will find in your home directory with that command in it.

Hope that helps,
GuitarFingers
Yes, thank you.  I played around with the .bash_profile earlier, unsuccessfully trying to set a new path.  I've since learned that the .bash_profile file is only read by a login shell and I have to use .bashrc to work in a non-login shell.  I'm a little hazy on what the difference is, and the different purpose for each.

Thanks,
Buck

---

