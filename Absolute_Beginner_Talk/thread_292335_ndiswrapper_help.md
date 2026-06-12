---
title: "ndiswrapper help"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by rockorager on 2006-11-03
Alright so I just installed Ubuntu 6.06.  I'm trying to get my Broadcom wireless adapter work, and through some research found out that ndiswrapper will do the trick.  I am attempting to install but can't seem to get my linux-headers to install.  Here is what I am doing:

```

sudo apt-get intall linux-headers-$(uname -r)

```

This prompt is giving me the following output:
```

Reading package lists... Done
Building dependency tree... Done
E:  Couldn't find package linux-headers-2.6.15-23-386

```

What should I do?

---

### Post by ishift on 2006-11-03
that looks a lot like the error i got for a specific repository.

what i did was i went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and downloaded and installed the packages from there. you just need to make sure you get the right files.

i hope that helps.

---

### Post by rockorager on 2006-11-03
Thanks...I found the package.  But how do I install the package?  Do I just put it in the /root directory?  It came with a folder and .deb file.

---

### Post by rockorager on 2006-11-03
Arg I should have tried first...still getting an error though

This time I open it with GDebi and it gives me the following error:

"Error:  Dependency is not satisfiable:  linux-headers-2.6.15-23"

How does one fix this?

---

