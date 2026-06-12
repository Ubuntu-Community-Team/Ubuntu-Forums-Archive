---
title: "trouble finding application directories"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by kendase3 on 2007-08-28
Hi everyone,

I'm having some more problems, unfortunately, and I can't seem to find my openoffice.org installation or openoffice.org SDK installation, which I need to find for an update of netbeans.  I've looked at some sites detailing what goes in the different folders but I'm still a little confused about where I could try finding common applications like openoffice, and if the SDK would be in the same place.  Thanks in advance.

---

### Post by forestpixie on 2007-08-28
you can use whereis

```
whereis whatyou'relookingfor
```

you can use locate, update the database first

```
sudo updatedb
```

```
locate whatyou'relookingfor
```

---

### Post by kendase3 on 2007-08-28
Thanks for the response!

This is what I get when I run whereis on "openoffice"

openoffice: /usr/bin/openoffice /etc/openoffice /usr/lib/openoffice /usr/X11R6/bin/openoffice /usr/bin/X11/openoffice /usr/share/openoffice /usr/share/man/man1/openoffice.1.gz

which of these is the location of the openoffice installation?  which is the location of the SDK?  I'm relatively new to Ubuntu so I find this file system a little more confusing than Windows.  Is there a "program files" equivalent, or are the programs all separated?

Thanks.

---

