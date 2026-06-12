---
title: "some problem"
date: 2012-11-25
forum: Any Other OS
---

### Post by Hasan55 on 2012-11-25
hey there, 
i am now running crunchbang linux 3.2.03-686- pae i686 which is based on debian but i have got some problems here .........i can not open youtube video page in my browser .........is  anything neccessary to install  open this page........please tell me what command should i use in terminal........


Another problem is i can not find software-centre here plz tell me how can i download useing terminal:(

---

### Post by Bucky Ball on 2012-11-25
*Thread moved to **Other OS/Distro Talk***

Note: Please, increase your chances of getting help and use descriptive thread titles. ;)

---

### Post by kiyop on 2012-11-26
I think you can get root privilege by
```
sudo su -
```and typing the password for ordinary user (which can use "sudo") on crunchbang.

You can use command:
```
apt-get update
apt-get install PACKAGE_NAME
```which is used to install packages in debian and which should be executed with root privilege, also in crunchbang.

Refer to
[http://qref.sourceforge.net/Debian/quick-reference/ch-package.en.html](http://qref.sourceforge.net/Debian/quick-reference/ch-package.en.html)
for more,
[http://www.debian.org/doc/manuals/debian-reference/ch02.en.html](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html)

I wonder if you can watch youtube videos after installing flashplugin-nonfree.
To install flashplugin-nonfree, you should add "contrib" at the end of the lines in /etc/apt/sources.list.
Refer to [http://wiki.debian.org/FlashPlayer](http://wiki.debian.org/FlashPlayer) and [http://wiki.debian.org/SourcesList](http://wiki.debian.org/SourcesList)
You can also refer to
[http://forums.debian.net/viewtopic.php?f=16&t=51504](http://forums.debian.net/viewtopic.php?f=16&t=51504)

> **Bucky Ball said:**
> Note: Please, increase your chances of getting help and use descriptive thread titles. ;)
+1

---

