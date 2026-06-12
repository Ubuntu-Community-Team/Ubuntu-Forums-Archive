---
title: "HELP: Unable to open folder"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by takuhii on 2007-06-22
I deleted some files from my **Downloads** (self made folder using the file manager in Ubuntu) folder in **Home**, now Ubuntu won't let me open my downloads folder anymore, it just hangs then after about 5 mins crashes and reloads the desktop... Any ideas?

---

### Post by buuntuu! on 2007-06-22
no idea, why x crashes. the only possible solution that comes to my mind is retrieving your data from the command line: move it to a new folder, delete the old one and see if the problem remains...
follow the link in my signature for command line basics, you'll need the commands cd, mv, rm, mkdir.
 it is quite easy ;)

---

### Post by wormser on 2007-06-22
Maybe it is a permissions issue.  If the folder is in your /home/username then try the following command.

```
ls -l ~
```

You can change the ~ with the full path.  The results should look something like this:

> drwxr-xr-x  4 username groupname    488 2007-05-18 01:30 downloads

More on permissions [here]("http://linuxcommand.org/lts0070.php").

This is just a guest and a trouble shooting step.

---

