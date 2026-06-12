---
title: "uninstalling after 'make install'"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-08-27
I have a source package and I have to 'make install' to install it. What happens if I want to remove it later?
Is there any way to monitor it to get all the files it installs? or maybe an easy way to make a .deb package using fakeroot, like i've seen done with java installers and the like?
Any help would be greatly apreciated.

---

### Post by Bachstelze on 2006-08-27
heh, *make uninstall* :)

---

### Post by PriceChild on 2006-08-27
As far as i know there is no easy way to uninstall from a "make install"

Most now reccomend that you use "checkinstall" instead which will create a deb archive for you, easily managed through any package manager.

---

### Post by richardward101 on 2006-08-27
Thanks for your reply, but unfortunately the source package i'm working with doesn't have uninstall defines as a target.

---

### Post by sbassett on 2006-08-27
> **richardward101 said:**
> I have a source package and I have to 'make install' to install it. What happens if I want to remove it later?
Is there any way to monitor it to get all the files it installs? or maybe an easy way to make a .deb package using fakeroot, like i've seen done with java installers and the like?
Any help would be greatly apreciated.

The easiest way would be to create the deb with checkinstall. This can be installed via synaptic or apt-get. Once this is installed, you simply go through the ./configure make routine, then use checkinstall in place of make install.

---

### Post by richardward101 on 2006-08-27
> **PriceChild said:**
> use "make checkinstall" instead which will create a deb archive for you, easily managed through any package manager.

Thanks, thats exactly what i wanted!

---

### Post by Bachstelze on 2006-08-27
So what the filesytem check is make unistall for ? Never ued it but I though it would do the trick :s

---

### Post by UbuWu on 2006-08-27
Get checkinstall from the repositories, it is perfect for situations like these.

---

### Post by PriceChild on 2006-08-27
> **HymnToLife said:**
> So what the filesytem check is make unistall for ? Never ued it but I though it would do the trick :s
I didn't even know there was an uninstall function to make :S

---

### Post by richardward101 on 2006-08-27
Quick question tho, when I run:
```
fakeroot checkinstall
```
I get ```
mkdir: cannot create directory `/usr/share/doc/brlcad-7.8.2': Permission denied

```
any ideas?

---

### Post by msak007 on 2006-08-27
Some apps include an unisntall script that's either placed in the app's folder once it's installed (for example /usr/local/<app name>/.uninstall), or is in the source folder where you compiled from. But for ease of use, I personally use and recommend checkinstall as others have suggested. Some apps fail using this method for one reason or another, but the overwhelming majority of apps I've compiled using it work and uninstallation is easy using Syanptic, apt-get, etc.

EDIT: You were posting at the same time and I just saw your post. You still have to prefix checkinstall with "sudo" - you're simply replacing "make install" with "checkinstall", so the command still has to be prefixed with sudo. The sequence would be```

./configure
sudo make
sudo checkinstall
```

---

### Post by richardward101 on 2006-08-27
thanks, it worked with sudo. Is there any way to get it working with fakeroot tho?

---

### Post by msak007 on 2006-08-27
> **richardward101 said:**
> thanks, it worked with sudo. Is there any way to get it working with fakeroot tho?

I've never used fakeroot so I can't really tell you how it's supposed to work. I'll read more about it, but is there an advantage to using fakeroot vs. sudo?

---

### Post by richardward101 on 2006-08-28
> **msak007 said:**
> I've never used fakeroot so I can't really tell you how it's supposed to work. I'll read more about it, but is there an advantage to using fakeroot vs. sudo?

Yes, as I can't always get root acces on the systems i'm using :)

---

### Post by sbassett on 2006-09-08
> **richardward101 said:**
> Yes, as I can't always get root acces on the systems i'm using :)

Have you tried

```
fakeroot checkinstall -D 
```

I would suggest doing everything within your homr dir, and of course, not using sudo.

---

