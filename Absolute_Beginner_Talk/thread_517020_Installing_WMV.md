---
title: "Installing WMV"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by SoyLoco911 on 2007-08-04
I just installed Ubuntu for the first time, and I wanted to be able to view wmv files. I read the below article(which shows you how to install mplayer), but I am not able to modify the sources.list file from that example. I created an administrator user, and that is who I am logged in as, but even as an administrator I can't edit the file. 
Any suggestions?

[http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html](http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html)

Thanks

---

### Post by buzzmandt on 2007-08-04
creating an admin user and staying as such is a bad idea, ubuntu and debian systems use sudo which is admin user for that one thing....log outa admin and return to your initial user mode and follow the following threads

[http://ubuntuforums.org/showthread.php?t=413624&highlight=how+to+enabling+multimedia](http://ubuntuforums.org/showthread.php?t=413624&highlight=how+to+enabling+multimedia)

---

### Post by wormser on 2007-08-04
Did you set up a root account or just an account for administration?  Root is the only account that will have access to modifying files.  Ubuntu recommends not to use root and instead use **sudo** and **gksudo** (for gui apps).  From the account that you set up during the install modify files by using those two commands in front of the command you are trying.  Here is an example from the link you provided.

```
gksudo gedit /etc/apt/sources.list
```

Since gedit is a gui app you use gksudo instead of sudo.  Now you can edit the file and save it.

---

