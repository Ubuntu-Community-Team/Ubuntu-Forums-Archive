---
title: "Messed up file permissions"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ghicking on 2007-10-29
I've managed to misuse 'chown' to make me the owner of all the files in the root directory and compounded the error by using -R.  However, the permissions are so jumbled that I can't change back.  If I use sudo in terminal, I get the error message 'sudo: must be setuid root'.  If I don't use sudo, I can run aptitude or apt-get (because I am now the owner instead of root), but not install anything because dpkg still requires root privileges.  Does anyone have a solution other than a reinstall?  (I have checked on the posts with similar titles, but nothing seems to be quite what I need)

Graham

---

### Post by hyper_ch on 2007-10-29
I think a re-install will be a lot quicker than fixing all of that...

---

### Post by Clickbg on 2007-10-29
Try to *su* and with root user change the ownership of the files, root user doesn`t need to be owner or to have access.

---

### Post by ghicking on 2007-11-02
Thanks for the support and advice.  I've managed to back up my Home file using a bootable CD and then reinstall.  I also managed to get the graphics sorted by reading what to do before I started instead of winging it.  Everything functional and stable now.

Graham

---

### Post by hyper_ch on 2007-11-05
Good to hear it's working now.

---

