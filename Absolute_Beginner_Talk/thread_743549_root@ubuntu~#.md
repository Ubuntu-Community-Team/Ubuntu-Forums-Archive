---
title: "root@ubuntu:~#"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by rkrakora on 2008-04-02
Good afternoon - 
I had to restart in safe mode after incorrectly tweaking my xorg.conf file.  I am sitting at the command line [shown in subject of this post], how do I get back to the booting process?
Rich

---

### Post by overdrank on 2008-04-02
> **rkrakora said:**
> Good afternoon - 
I had to restart in safe mode after incorrectly tweaking my xorg.conf file.  I am sitting at the command line [shown in subject of this post], how do I get back to the booting process?
Rich

You can try the command ```
startx
```
Then you may try and reconfigure you xorg with this command ```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by aysiu on 2008-04-02
Actually, if you boot into regular mode, you should be able to edit the xorg.conf file from that command-line, too (rkrakora@ubuntu:~$)

Boot into regular mode and log in: ```
cd /etc/X11
``` will get you to the right directory. ```
ls
``` will list the directory's contents. Hopefully, you have a working backup of the xorg.conf file. For the sake of this example, let's say it's called *xorg.conf.bak*. If that's the case, you would type ```
sudo mv xorg.conf xorg.conf.not.working
``` and then ```
sudo cp xorg.conf.bak xorg.conf
``` This last command should restore your working backup. Then you can ```
sudo /etc/init.d/gdm restart
``` to activate the X server again.

---

### Post by rkrakora on 2008-04-02
Thank you for your help, I will try both of these suggestions!

R.

---

