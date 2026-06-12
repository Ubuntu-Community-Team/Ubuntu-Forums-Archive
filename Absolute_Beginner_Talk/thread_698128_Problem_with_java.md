---
title: "Problem with java"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by ZeroFive1 on 2008-02-15
First, I got the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When trying to install an update.

This happened before, and I ran

sudo dpkg --configure -a

which seemed to fix it, but this time I got:

$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

This might be because I was messing with trying to get java to work recently. Also, sun-java6-plugin doesn't exist in my synaptic either. Help?

---

### Post by emarkd on 2008-02-15
Did you enable the universe and multiverse repositories?  In Synaptic, click on Settings > Repositories and check them.  Reload and it should all be there.

---

### Post by ZeroFive1 on 2008-02-15
I solved the dpkg --configure -a problem, but yes I do have universe and multiverse enabled, and it still doesn't show sun-java6-plugin. Everything else in sun-java6 is there, but not plugin.

---

### Post by emarkd on 2008-02-15
Hmm...I seem to have it in Multiverse from here.  Are you using Synaptic or the command line?  Try

```
sudo apt-get install sun-java6-plugin
```

and see what you get.

---

### Post by ZeroFive1 on 2008-02-16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

D:

I have no idea what happened. I really hope I don't have to reinstall ubuntu.

---

### Post by dhruva023 on 2008-02-16
just go to syneptic, and remove "jdk-6-doc" packge.
it will solve the problem.

I had the same problem.

---

### Post by ZeroFive1 on 2008-02-16
For the plugin problem?

I shall try.

Thanks.

---

### Post by ZeroFive1 on 2008-02-16
Yeah, it doesn't help. I'm also running on a AMD64 machine if it makes a difference.

---

### Post by ZeroFive1 on 2008-02-18
Is there any way I can manually edit my sources to allow the plugin to show?

---

