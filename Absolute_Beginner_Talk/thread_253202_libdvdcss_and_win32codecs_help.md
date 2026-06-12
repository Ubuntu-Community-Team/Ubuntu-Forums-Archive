---
title: "libdvdcss and win32codecs help"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2006-09-08
Does anyone know where i can get "libdvdcss 1&2" and "win32codec". Im not sure which sources I need to add to synaptics.

---

### Post by aysiu on 2006-09-08
This should help:
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by Loki57701 on 2006-09-08
I went to my: /etc/apt/sources.list and added the PLF repositories but when I tried to save it I got an error saying I didnt have permission. Which I find interesting because Im the admin and the only  user? I tried right clicking the file-system icon and went to properties>permissions and selected the owner write option but It gave me the same error. So why cant I have write access to my own hard drive, what dumb noob mistake did I make this time? lol

---

### Post by jordanmthomas on 2006-09-08
You are not the only user on your system.

You need to edit your /etc/apt/sources.list as another user:  root
Root is really the admin, and you just get rights to root's privileges to err...administrate.

Press Alt+F2 and type this:
```
gksu gedit /etc/apt/source.list
```
It will prompt you for your password and you will be editing the file as root, (which is who owns the file)

---

### Post by yourearthlymaster on 2006-09-08
try sudo in the terminal if that doesn't work.  otherwise, all should be good, still a newb so not too sure though.

---

### Post by aysiu on 2006-09-08
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by yourearthlymaster on 2006-09-08
Thanx for the link, I didn't know that.

---

### Post by Loki57701 on 2006-09-08
tried: (gksu gedit /etc/apt/source.list) from RUN

and

(sudo gksu gedit /etc/apt/source.list) from the terminal

then did an: (apt-get update) and I didnt see any of the PLF repositories being updated. But I still tried: (sudo apt-get install libdvdcss2 w32codecs
) and I got:

(Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate)
--------------------------------------------------------------------

is there anything Im doing wrong here?

---

### Post by Loki57701 on 2006-09-08
I followed the guide on: [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

then tried adding the PLF repositories and it worked.....

thx for all your help

---

### Post by aysiu on 2006-09-08
When you edit your sources.list, you actually have to put the sources in.

And... more importantly, you want to edit the /ec/apt/source**s**.list, not the /etc/apt/source.list.

---

