---
title: "Removing Kubuntu boot screen from Gnome"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by GI_Josh on 2007-03-09
Hi guys.  I recently installed kde onto my ubuntu installation just to see what was on the other side of linuxdom.  After playing around with it for a few days, and switching back and forth between kde and gnome, I decided that I wasn't a huge fan of kde, so I wanted to uninstall it and stick with strictly gnome.  I used aptitude to install, so I used aptitude to remove it as well.  All the programs are gone, however, when I boot up ubuntu, I still see the kubuntu boot screen with the progress bar, and not ubuntu's.  It doesn't affec the performance of my ubuntu in any way, but it is just annoying :-)

Is there any way I can change this back to say ubuntu?

---

### Post by lamalex on 2007-03-09
did you try apt-get remove kdm && apt-get install gdm?

---

### Post by happy-and-lost on 2007-03-09
*sudo apt-get install usplash-theme-ubuntu* (I think (Currently at a Debian machine), do a Synaptic searc for "ubuntu" and install the corresponding usplash)

---

### Post by o_fortuna on 2007-03-09
It's not too difficult at all: just follow the instructions I gave here: [http://www.ubuntuforums.org/showthread.php?t=378869]("http://www.ubuntuforums.org/showthread.php?t=378869")

Also, have you made sure that kubuntu-artwork-usplash has been completely removed through synaptic?

---

### Post by GI_Josh on 2007-03-10
I did this:
$sudo update-alternatives --config usplash-artwork.so
From here:
[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)
and I get this:
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
update-alternatives: unable to open /var/lib/dpkg/alternatives/usplash-artwork.so.dpkg-new for write: Permission denied

What is going on?  Also, there is no ubuntu usplash in my synaptic, but there are ones for kubuntu (removed) and xubuntu.

---

### Post by GI_Josh on 2007-03-11
bump

---

### Post by msak007 on 2007-03-11
The instructions o_fortuna should have worked. The Ubuntu usplash theme is named different from the others. All the other *buntu distros use the format "(K)(X)(Ed)ubuntu-artwork-usplash", but Ubuntu's is called **usplash-theme-ubuntu**. Check in Synpatic first to see if it's installed, and if it is try to force a reinstall. The fact that if finds /usr/lib/usplash/usplash-default.so doesn't mean anything - that's just a symlink to the actual usplash theme and is always there regardless of what theme you use. If you were to navigate to /usr/lib/usplash and do an ls -l, you would see something like 

```
rwxrwxrwx 1 root root      36 2007-02-03 11:05 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
```Then going to /etc/alternatives and again doing ls -l, you'll see something like this (the theme may vary, I use Kubuntu):

```
lrwxrwxrwx 1 root root  41 2007-03-11 16:09 usplash-artwork.so -> /usr/lib/usplash/usplash-theme-kubuntu.so
```

---

### Post by r4ik on 2007-03-11
Change the /etc/X11/default-display-manager file. For KDM, the file should read /usr/bin/kdm; for GDM, the file should read /usr/sbin/gdm

Good luck !

From: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

---

### Post by msak007 on 2007-03-11
> **r4ik said:**
> Change the /etc/X11/default-display-manager file. For KDM, the file should read /usr/bin/kdm; for GDM, the file should read /usr/sbin/gdm

Good luck !

From: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
If I'm not mistaken, I believe he was talking about usplash and the theme that he sees while the OS is loading (hence the progress bar), not the login manager that he sees once X loads.

---

### Post by r4ik on 2007-03-11
> **msak007 said:**
> If I'm not mistaken, I believe he was talking about usplash and the theme that he sees while the OS is loading (hence the progress bar), not the login manager that he sees once X loads.

Thanks for the correction i am heading for soap and toothbrush now.
Sorry.

---

### Post by mburdess on 2007-07-09
Hi could you tell me how I could change the Ubuntu boot screen. I have made a picture I want to use as boot screen.

---

