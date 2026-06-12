---
title: "How do i uninstall amsn (Autopackage)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-02-04
I installed it using autopackage and no i can't remove it.

I looked under system tools for manage 3rd party software but it's not there.

Please help!

---

### Post by jken146 on 2008-02-04
[http://autopackage.org/faq.html](http://autopackage.org/faq.html) tells me that there is a **package** command with which you can uninstall autopackages.  If you type ```
man package
``` you should get more info.

I would recommend using the official Ubuntu repositories and the associated tools (Add/Remove, Synaptic, apt-get etc.).

---

### Post by Cypher on 2008-02-04
Nevermind..

---

### Post by thedon_1 on 2008-02-04
> **jken146 said:**
> [http://autopackage.org/faq.html](http://autopackage.org/faq.html) tells me that there is a **package** command with which you can uninstall autopackages.  If you type ```
man package
``` you should get more info.

I would recommend using the official Ubuntu repositories and the associated tools (Add/Remove, Synaptic, apt-get etc.).



I tried using package list as they suggested, but still nothing
Looked through the site and whenever i try something they suggest using amsn as the package name i get not found.

---

### Post by jken146 on 2008-02-04
I don't know how autopackage works I'm afraid.  Still, check that the package you installed was called **amsn** and try reading the manpage I directed you to.

---

### Post by thedon_1 on 2008-02-04
Bump

---

### Post by Bad_Byte on 2008-02-05
```
package remove amsn
``` at command line

---

### Post by thedon_1 on 2008-02-05
Says failed, package not found

---

### Post by mickeelm on 2008-02-16
That is strange, it worked perfectly for me. However if I run the command again (did it just to test), I get that message. I'm sure you already have but, have you tried

```
sudo apt-get remove amsn
```

? Cause it never says in the thread that you have...since you installed with autopackage it shouldn't work but well, if something strange happened or so, and you won't lose many seconds of your life trying :)

EDIT: Try to run the installation program again (with autopackage) and then try to remove it, makes a difference sometimes for a reason which I do not know.

---

