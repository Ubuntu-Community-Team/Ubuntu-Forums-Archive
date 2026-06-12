---
title: "changing user rights"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by dodgeman79 on 2006-01-20
new here and first time Ubuntu user.  I've read and searched these forums and another site.  great information to get me going.

problem is the user I created during install doesn't have superuser rights to further set up Ubuntu.  would like to know how to get user to have same privilages and rights as root, if possible.

---

### Post by 23meg on 2006-01-20
Welcome on board. You should use sudo.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by JNowka on 2006-01-20
if you are doing it from the command line in konsole then try the following

sudo <command>
Password: your password

sudo will work for 15 minutes and you have to put it infront of every command that involves changing the system.

sudo su
Password: your password

this will work until you close out that instance of the konsole and you do not need to put sudo infront of every command.

---

### Post by dodgeman79 on 2006-01-20
I called a friend who knows linux and we figured out that I needed to use visudo to edit the sudoers file to give my name full rights.

thanks for the help and link

---

