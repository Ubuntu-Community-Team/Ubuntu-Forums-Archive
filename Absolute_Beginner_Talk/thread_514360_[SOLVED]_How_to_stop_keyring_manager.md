---
title: "[SOLVED] How to stop keyring manager"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by jessi3k3 on 2007-07-31
Hello guys. I'm using Ubuntu 7.04. Whenever I connect to a secure network and enter the network key I'm asked to enter my Keyring password. I guess the network key is stored in the Keyring manager. How can I disable this? Everytime I connect to my secure home network (couple of times a day) i'm asked to enter my keyring password and this is very annoying. Is there a way to store a wireless key without confirming a separate password every time?

---

### Post by aysiu on 2007-07-31
Try [this](http://ubuntuforums.org/showpost.php?p=2545332&postcount=71).

---

### Post by Majorix on 2007-07-31
```
sudo apt-get install libpam-keyring
```

```
sudo gedit /etc/pam.d/gdm
```

Add this:
```
@include common-pamkeyring
```

```
sudo reboot
```

When you are back you will be asked for the key for the last time.

---

### Post by lisati on 2007-07-31
There's also [http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring) which, amongst other things, discusses some of the ideas already mentioned.

---

### Post by Majorix on 2007-07-31
> **aysiu said:**
> Try [this](http://ubuntuforums.org/showpost.php?p=2545332&postcount=71).

My /etc/pam.d/gdm doesn't look like that but it still works? I believe what you have to add is what I typed in here... But can't be sure.

---

### Post by jessi3k3 on 2007-07-31
> **aysiu said:**
> Try [this](http://ubuntuforums.org/showpost.php?p=2545332&postcount=71).

Ah! The file is read only. How do I save it. It says I dont have access.

---

### Post by lisati on 2007-07-31
> **jessi3k3 said:**
> Ah! The file is read only. How do I save it. It says I dont have access.

If you're using something like GEDIT from the terminal, you might have to use sudo to be able to save it, e.g.
```

sudo gedit <filename>

```

Don't be alarmed if it asks for your password and nothing shows when you type it in - your password will still be registered.

---

### Post by aysiu on 2007-07-31
Alt-F2 and paste in this line ```
gksudo gedit /etc/pam.d/gdm
``` then hit **Enter**

---

### Post by jessi3k3 on 2007-07-31
Thank you very much. It seems to be working now.

---

### Post by jessi3k3 on 2007-08-02
Guys I need help. After just booting ubuntu today again Not only do I have to enter my password twice during login, it still asks for my keyring password. For a second I thought the problem was fixed :confused:

---

### Post by heffo_j on 2007-08-03
Hi there folks,

I've followed both Aysiu's lead and Majorix's advice and get the following problems:

1) I have to enter my password twice at the sign-in screen on boot up to open my OS.

2) There has been no effect with the sign-in to the network; I still have to sign in.


EDIT: I have since redone Majorix's suggestion BUT putting the inserted line at the bottom of the list, rather than at the top. What has this achieved? Not much. It did stop the double password sign-in after boot up. I still have to sign-in the network...... I'll keep playing with it until it either breaks or works.

EDIT 2: Linux Mint Forums made it clear for me. Try this link. Notice is points back to Ubuntu but the initial explanation did the trick for me:

[http://www.linuxmint.com/forum/viewtopic.php?highlight=keyring&t=3372]("http://www.linuxmint.com/forum/viewtopic.php?highlight=keyring&t=3372")




Regards
John

---

