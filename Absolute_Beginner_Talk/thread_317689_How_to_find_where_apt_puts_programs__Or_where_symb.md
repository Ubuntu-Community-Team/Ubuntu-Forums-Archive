---
title: "How to find where apt puts programs?  Or where symbolic links originate from?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-12-12
Hi,

I just used apt-get to install Bugzilla.  I see that the installation creates a symbolic link to a /etc/bugzilla/ directory, but how can I locate the actual directory.  How does one trace a symbolic link to its origins?

Thanks!

---

### Post by Zelut on 2006-12-12
on the command line you can try "ls -l" and it should show you the destination of any symbolic links (if I remember right).

Does that help?

---

### Post by kpm on 2006-12-12
> **kuyaedz said:**
> on the command line you can try "ls -l" and it should show you the destination of any symbolic links (if I remember right).
Does that help?

Thanks for the quick response... I was having a bit of an idiot momnet... or one of those id10t errors... I am using a windows scopy utility and couldn't figure out where the files were I was looking for, since in the terminal window I could see them but on the client on Windows, could not, so I assumed a symlink and malfunctioning client... turns out there is this button called 'refresh' *sigh*.
thanks anywho.

---

