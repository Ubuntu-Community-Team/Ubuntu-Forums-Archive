---
title: "Error message in terminal for VLC streaming video code"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-15
I have been trying configure my VLC, I used this code from the ubuntu wiki page:


    * Inorder to stream video via vlc, you also need to install the following packages. 

apt-get install avahi-daemon
apt-get install avahi-utils

This is the message it gives me each time.

me@me-laptop:~$ apt-get install avahi-daemon
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@me-laptop:~$ apt-get install avahi-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
me@me-laptop:~$


...I am the only user on this notebook so I thought I was root, can some one help me with this please.

thanks,
-c.

---

### Post by taurus on 2006-10-15
Run them with sudo...

```

sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils

```

---

### Post by kingjere on 2006-10-15
First:
Taken From [https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

The root user in GNU/Linux is the user which has administrative access to your system. Normal users do not have this access for security reasons. However, Ubuntu does not include the root user. Instead, administrative access is given to individual users, who may use the "sudo" application to perform administrative tasks. The first user account you created on your system during installation will, by default, have access to sudo. You can restrict and enable sudo access to users with the Users and Groups application (see the section called “Users and Groups” for more information).

When you run an application that requires root privileges, sudo will ask you to input your normal user password. This ensures that rogue applications cannot damage your system, and serves as a reminder that you are about to perform administrative actions which require you to be careful!

To use sudo when using the command line, simply type "sudo" before the command you wish to run. Sudo will then prompt you for your password.

Sudo will remember your password for a set amount of time. This feature was designed to allow users to perform multiple administrative tasks without being asked for a password each time. 

then:
man sudo

---

### Post by crimesaucer on 2006-10-15
oh my god, I didn't notice that there was no "sudo" apt-get in the code on I was pasteing from the wiki page, thanks, I'll give it a try right now.

**everything installed perfectly, thanks again.

---

