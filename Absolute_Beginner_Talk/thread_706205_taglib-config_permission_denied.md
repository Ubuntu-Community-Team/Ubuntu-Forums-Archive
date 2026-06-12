---
title: "taglib-config permission denied"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by maniheer on 2008-02-24
Hi, I'm trying to install gomastage from using this command

svn checkout [http://gomastage.googlecode.com/svn/trunk/](http://gomastage.googlecode.com/svn/trunk/) gomastage-read-only

and I keep on getting the error taglib-config permission denied after doing make -f Makefile :confused:

HELP

---

### Post by y-lee on 2008-02-24
Permission problems usually mean you need to run the command as superuser.

if **make -f Makefile** is the right command try

```
sudo make -f Makefile
```


**Note:** you will prompted for your password, enter it even tho the prompt doesn't move it will be entered :)

---

### Post by maniheer on 2008-02-24
Thanks for your reply but putting 'sudo make -f Makefile' and entering my password gave me the same problem.:(:(:(

By the way, the same problem happened with 'xml2-config', with the same app but that doesn't come up anymore.:confused:

---

### Post by y-lee on 2008-02-24
> Thanks for your reply but putting 'sudo make -f Makefile' and entering my password gave me the same problem

I assume you have a file in that directory called Makefile, go to that folder in Nautilus (ie the file manager) and right click it and choose Properties, click on the permissions tab and make sure you are the owner and have permission to read write and execute that command.

---

