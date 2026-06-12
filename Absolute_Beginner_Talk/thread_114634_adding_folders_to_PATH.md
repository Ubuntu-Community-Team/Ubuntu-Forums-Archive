---
title: "adding folders to PATH"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by hobbes_opus on 2006-01-09
Its been a long time since I've used a Unix system - I guess the .profile file is gone.  How do I (permanently) add a directory to the PATH?

Also, it seems that PATH does not include home, is that on purpose?  Shouldn't it usually include home?

 I can't seem to get the Java plugin working, and I think that's the problem.

Thanks,
Bob

---

### Post by aysiu on 2006-01-09
I think "the PATH" is anything in /usr...
/usr/bin
/usr/local/bin
are two examples.

---

### Post by shadesfox on 2006-01-09
the .profile doesn't exist anymore, but .bash_profile does.  .bash_profile does include ~/bin so if you have /home/(user)/bin that will be in the path.  But if you want, you can tack onto the end of .bash_profile something like 'export $PATH:/your/own/path/'

---

### Post by hobbes_opus on 2006-01-09
Ok, I guess that didn't work.  I'm trying to get Java working in my mozilla brower (and firefox for that matter).  I've followed all the instructions, including the one that said to install it in home if /usr/java is not in the path.  Any other ideas?

---

### Post by 5-HT on 2006-01-09
[QUOTE=hobbes_opus]Its been a long time since I've used a Unix system - I guess the .profile file is gone.  How do I (permanently) add a directory to the PATH? [/QUOTE]

Hi, I've always followed the convention of putting changes like this within .bashrc...maybe this will help?

To append to the PATH variable and make it permanent all you need to do is enter the following in your .bashrc file in your home directory (~/.bashrc).
 ```
export PATH=$PATH:<add new path here>
```

IMPORTANT! -make sure you include the '$PATH' portion as that simply completes to all of the directories you already have in your path.

So if you leave out '$PATH' and just enter the one you want, all others will be gone (not the directories...just their inclusion in PATH).

After that all new entries you want need to be separated by a colon (without any spaces between colons and entries).

If you don't want it to be permanent, instead of adding it in ~/.bashrc, simply enter it in a terminal (it'll only take effect in that current subshell).


HTH

---

