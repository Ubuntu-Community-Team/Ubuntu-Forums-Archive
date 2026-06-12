---
title: "File Shredder?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Imashinu on 2007-08-15
Does ubuntu have a built in file shredder like PC linux OS 07. If not, are there any secure alternatives.

---

### Post by HereInOz on 2007-08-15
Have a look at either secure-delete or wipe.  Both are available in the repositories, although not supported by Ubuntu.

---

### Post by Imashinu on 2007-08-15
I downloaded secure delete but can someone walk me through operation of it?

---

### Post by mali2297 on 2007-08-15
The command is *srm* which is run in the terminal (compare with *rm*):

```

srm filename

```

Check *man srm* for more information.

---

### Post by shad0w_walker on 2007-08-15
Like lots of commands in Linux this is a very obvious one. The command to shred a file is 

```
shred <whatever file>
```

Defaults to 25 overwrites with random data. If you add the -z and -u options to the command it overwrites with zeros with 0s and then deletes the file.

---

### Post by mali2297 on 2007-08-15
The tool *srm* is part of the *secure delete* package whereas *shred* is an old unix command. I don't know, but I believe *shred* is less secure on modern file systems.

---

### Post by shad0w_walker on 2007-08-15
Shred is less secure on certain configurations of file systems, however for the most part it is still very secure. I only bothered to post it up to offer some other choices and perhaps offer features/options that srm doesn't have. Not familiar with srm so don't know if there is anything different but it never hurts to have some other choices.

---

### Post by mali2297 on 2007-08-15
After doing some research, it seems like an entirely secure deletion on ext3 is impossible. So, *srm* is perhaps not that much better than *shred*.

---

### Post by Hospadar on 2007-08-15
If you want some extra security, you may want to also shred/delete the indexes in ~/.beagle and/or ~/.Tracker (that is if you use beagle or Tracker to do indexing)

---

