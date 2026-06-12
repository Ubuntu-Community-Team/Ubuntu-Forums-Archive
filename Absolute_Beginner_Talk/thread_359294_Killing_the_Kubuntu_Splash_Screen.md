---
title: "Killing the Kubuntu Splash Screen"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-11
Hi!  I recently installed the Kubuntu desktop, only to find myself uinstalling it shortly after.  I have successfully removed the kubuntu-desktop and returned the login screen to Gnome.  However, when I first select Ubuntu from Grub, the Kubuntu splash screen pops up rather than the Ubuntu one.  I know it is trivial, but can this be fixed?

---

### Post by Co.Sinecure on 2007-02-11
Try having a look at [www.psychocats.net](www.psychocats.net) and clicking on the 'Pure gnome' link (assuming you're running regular ubuntu. It will list all the packages to remove to get back to the pure gnome install.

Also a ```
sudo dpkg-reconfigure gdm
``` might do it?

---

### Post by Darklighter137 on 2007-02-11
Thank you for your suggestions.  I've already used the second thing to recover my login manager, and according to aptitude, it seems as though the ksplash package no longer exists.  When I typed "sudo aptitude remove kslpash", it told me that nothing would be removed (when I searched for the ksplash package, a c appeared next to its name, if that helps any).  :confused:

---

### Post by Lukeg on 2007-02-11
This happened to me as well, though I was able to uninstall ksplash with synaptic.

You may also want to try reinstalling usplash and usplash-theme-ubuntu.

---

### Post by Tahir on 2007-03-05
Found it!

I was looking for this too and I found a webpage* on it.  All you do is open a terminal, then type 
```

sudo update-alternatives --config usplash-artwork.so
```

after selecting your splash screen, then type:

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Worked for me :)

-Tahir

*[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

---

### Post by Darklighter137 on 2007-03-06
Thanks!

---

