---
title: "synaptic/apt-get broken?"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by roadman555 on 2007-02-04
I just installed Ubuntu 6.10 and the installation went fine.
Clean install, no dualboot, fresh harddrive.

Right after installing it had over 100 updates available. I let it do the updates. Then it froze during the install of the updates. I restarted X (ctrl-alt-backspace) and was able to log in. I was insructed to type the following in terminal:

 dpkg --configure -a

which told me to go to synaptic and fix broken packages. I did and it said it was successful.
Now, I keep getting segment fault (core dumped) anytime I try to install a .deb package, apt-get command and try to run synaptic. Here is a screenshot. Thanks for any help.

---

### Post by roadman555 on 2007-02-04
Here is what I got when I tried to run add/remove :

jeff@jeff-ubuntu:~$ gnome-app-install
Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 

** (gnome-app-install:9847): WARNING **: return value of custom widget handler was not a GtkWidget
Segmentation fault (core dumped)
jeff@jeff-ubuntu:~$



And when I tried to run update manager:

jeff@jeff-ubuntu:~$ update-manager
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files) 
Segmentation fault (core dumped)
jeff@jeff-ubuntu:~$ 


Thanks

---

### Post by taurus on 2007-02-04
Edit /etc/apt/sources.list 

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save it and run

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by roadman555 on 2007-02-04
Thanks!  It appears to be updating just fine and so far no more errors or freezing up.

Once again, a big THANK YOU!

---

### Post by mooter on 2007-02-08
Cool, that helped here too.
I searched a bunch and most of it seemed Samba related, but I never downloded it, so this was the answer.
Yeyah

---

