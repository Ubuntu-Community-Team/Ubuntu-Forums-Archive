---
title: "uninstalling programs no through add/remove"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-07-16
How does one uninstall programs that where installed not through the add/remove feature?

---

### Post by AlexenderReez on 2007-07-16
synaptic or adept

---

### Post by shearn89 on 2007-07-16
I think Akuma's saying he (she) didn't install with synaptic. If you compiled from source you can cd to the directory and run ```
sudo make uninstall
```

When compiling from source i tend to use ```
sudo checkinstall
```, as this adds the packages to the package manager.

---

### Post by phr0ze on 2007-07-16
I guess what everyone is saying is if you don't use add/remove or synaptic to manage all your apps, then you have to remember the method you used to install each individual program so you can then figure out the command to uninstall it. There is no unified way to uninstall programs which aren't added through synaptic/apt system.

---

### Post by Akuma Shiro on 2007-07-21
I downloaded the AVG linux anti-virus program, and then I clicked on the .deb link to download, it said it could open with an install program from the archive. It installed, but now I can not find the installed program anywhere in my system, so I want to uninstall it. I tried all the ways mentioned, but the terminal just says that those commands are not found.

---

### Post by por100pre1 on 2007-07-21
You'll find it in Synaptic.

---

### Post by por100pre1 on 2007-07-21
I think this should work:

```
sudo apt-get remove avg75fld
```

---

### Post by Akuma Shiro on 2007-07-22
It was in synaptic. Thanks.
Am I understanding correctly, that when I install an app that is not from add/remove, it will appear in synaptic?

---

### Post by jvc26 on 2007-07-22
Only if it is a .deb file, if you compiled from source it won't be there.
Il

---

### Post by Akuma Shiro on 2007-07-22
Cool.
What does it mean to "compile from source"?

---

### Post by Malibu Illusion on 2007-07-22
Usually, to download a tarball and run through compile, make and make install.  Sometimes manually compiling source files with gcc if needed.  In other words, without using packages.

---

### Post by Junkhead on 2007-07-22
When one "compiles from source", they take the source code of the program and  turn it into a form the computer can understand.  Users usually don't need to do that, and can instead install through synaptic or a given .deb file for Ubuntu in this case.

---

### Post by Akuma Shiro on 2007-07-23
Ok. So chances are that I will probably never do that. I would like to learn how, but I'm sure that  the time will come.
Thanks once again for everyones help. I hope to one day return the favor.:popcorn:

---

