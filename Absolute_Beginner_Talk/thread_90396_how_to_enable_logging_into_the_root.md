---
title: "how to enable logging into the root"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by infamous-online on 2005-11-14
hey guys, i've run into a problem. with me being so used to distros such as, suse and fedora, where you could login with the root account.

i am trying to delete a few files and folders, but since i am not command line type of guy, i always login as the root to perform the task. 

to my suprise ubuntu has disabled logging in the root account, even though i've set the password and everything, so i am wondering how can i log into the root account, so i can remove some files and folders to the trash can so i can delete them.

please don't flame me, since i not an expert when it comes to command line stuff,so hopefully i can find the answers or tips here.

i hope i didn't confuse any of you guys. :???:

---

### Post by adwait on 2005-11-14
try
```
sudo gdmsetup
```

Enable root graphical login from there. gdmsetup is also there in the gnome menu.....but can't remember what its called :)

---

### Post by 23meg on 2005-11-14
Welcome to the forums. Logging on as root isn't recommended. If you want to do it anyway, here's how to enable it: ```
sudo passwd root
``` and then System / Administration / Login Screen Setup / Security / Allow root to login with GDM.

There's a more practical way of deleting a few files and folders: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Here's a flame war that resulted from this same question being asked: [http://ubuntuforums.org/showthread.php?t=86811](http://ubuntuforums.org/showthread.php?t=86811)

Here's the forum search function that you should use before asking questions: [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php) . It's also conveniently located on the top bar.

---

