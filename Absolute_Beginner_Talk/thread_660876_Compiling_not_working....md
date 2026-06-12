---
title: "Compiling not working..."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-07
I'm trying to compile Moblock but it gives me an error. 

```
erik@erik-desktop:~/Desktop/MoBlock-0.8$ sudo make install
install -m 755 moblock /usr/bin
install: cannot stat `moblock': No such file or directory
make: *** [install] Error 1
erik@erik-desktop:~/Desktop/MoBlock-0.8$ 


```

---

### Post by spiderbatdad on 2008-01-07
have you tried ```
sudo ./Desktop/MoBlock-0.8.sh
```

yes build-essential is needed from synaptic, as "ajgreeny" says below.

---

### Post by ajgreeny on 2008-01-07
Have you installed **build-essentials**?  It is needed, I think, to do any of the sort of things you're trying to do.

---

### Post by PeterJS on 2008-01-07
By the time you've gotten to make install failing on you, you've already used the vast majority of the build essential tools (make, gcc, and all the needed dev files).

Good news bad news. Good news MoBlock is built and usable, bad news is it's not in a standard location. You could leave it where it is and use it in place. Move the whole thing over to /opt/ and symlink the progams themselves in to /usr/local/bin. Or try and trouble shoot the make install issues and get it where it's supposed to be.

I don't know if it would fare any better, but you might try installing checkinstall. It's a replacement that wraps make install (or ./install.sh, if it's used instead) and builds a deb package out of it. It might be happier installing to an empty environment of the package builder, and if it worked it'd be cleaner over all for the system.

---

