---
title: "How to log in as &quot;root&quot;."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by dninex on 2007-06-29
When I try to access some files or write in certain folders, a message pops up saying that I have no privilege to do so. I heard that I have to access as a "root" at that point, but I have bo clue on how to do so. Can anyone provide instructions on how to do so? Thanks.

---

### Post by bodhi.zazen on 2007-06-29
Use sudo: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

so sudo <command_to_run_as_root>

Or to be root : ```
sudo -i
```

---

### Post by Atomic Dog on 2007-06-29
I thought sudo su was the only way to be root.  You learn something new every day...

---

### Post by wondering_jew on 2007-06-29
Well if you just want to manipulate files and folders and such just open up a terminal and type 

sudo nautilus

enter your password and nautilus will open with root access to files and folders. 
Of course be careful anytime you are doing anything as root, but this will let you do what you need to.

---

### Post by tarek on 2007-06-29
I just posted an easy way use root with GUI a few minutes ago:
[http://ubuntuforums.org/showthread.php?p=2932500#post2932500]("http://ubuntuforums.org/showthread.php?p=2932500#post2932500")

tk

---

### Post by bodhi.zazen on 2007-06-29
> **wondering_jew said:**
> Well if you just want to manipulate files and folders and such just open up a terminal and type 

sudo nautilus

enter your password and nautilus will open with root access to files and folders. 
Of course be careful anytime you are doing anything as root, but this will let you do what you need to.

If you run graphical programs as root, you should use gksudo :

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **tarek said:**
> I just posted an easy way use root with GUI a few minutes ago:
[http://ubuntuforums.org/showthread.php?p=2932500#post2932500]("http://ubuntuforums.org/showthread.php?p=2932500#post2932500")

tk

And a fine how-to it was too :)

---

