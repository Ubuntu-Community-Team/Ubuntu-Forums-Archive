---
title: "stream ripper"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Manoau2002 on 2006-05-04
I am new to linux and I am trying to install streamripper. I tried install it through the automatix program twice but it never appeared installed under the sound menu. I downloaded the .deb file from the debian website and I tried to install it using the terminal. This is what my attempt looked like:

manoau2002@ubuntu:~$ cd ~/Desktop
manoau2002@ubuntu:~/Desktop$ sudo dpkg -i streamripper_1.61.7-1_i386.deb
Password:
Selecting previously deselected package streamripper.
(Reading database ... 72160 files and directories currently installed.)
Unpacking streamripper (from streamripper_1.61.7-1_i386.deb) ...
Setting up streamripper (1.61.7-1) ...
manoau2002@ubuntu:~/Desktop$

After this process was complete I again returned to the sound menu but it still wasn't there. 

Any ideas?

                            Thanks

---

### Post by jazzmuzik on 2006-05-04
You should try installing the Ubuntu version which is in the repostories before trying a Debian package. There may be slight differences like menus, etc.

[http://packages.ubuntulinux.org/breezy/sound/streamripper](http://packages.ubuntulinux.org/breezy/sound/streamripper)
[http://packages.ubuntulinux.org/dapper/sound/streamripper](http://packages.ubuntulinux.org/dapper/sound/streamripper)
[http://packages.ubuntulinux.org/warty/sound/streamripper](http://packages.ubuntulinux.org/warty/sound/streamripper)

---

### Post by arnieboy on 2006-05-05
[QUOTE=Manoau2002]I am new to linux and I am trying to install streamripper. I tried install it through the automatix program twice but it never appeared installed under the sound menu. I downloaded the .deb file from the debian website and I tried to install it using the terminal. This is what my attempt looked like:

manoau2002@ubuntu:~$ cd ~/Desktop
manoau2002@ubuntu:~/Desktop$ sudo dpkg -i streamripper_1.61.7-1_i386.deb
Password:
Selecting previously deselected package streamripper.
(Reading database ... 72160 files and directories currently installed.)
Unpacking streamripper (from streamripper_1.61.7-1_i386.deb) ...
Setting up streamripper (1.61.7-1) ...
manoau2002@ubuntu:~/Desktop$

After this process was complete I again returned to the sound menu but it still wasn't there. 

Any ideas?

                            Thanks[/QUOTE]
streamripper does not create a menu entry. run it from terminal as:
```
streamripper
```

---

