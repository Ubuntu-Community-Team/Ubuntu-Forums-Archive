---
title: "Apt-get : command not found"
date: 2012-02-08
forum: Any Other OS
---

### Post by shankarvalleru on 2012-02-08
HI,

My linux machine does not have apt-get support. Could anybody tell me how can I install the apt-get command itself ?

Thanks,

---

### Post by matt_symes on 2012-02-08
Hi

> **shankarvalleru said:**
> HI,

My linux machine does not have apt-get support. Could anybody tell me how can I install the apt-get command itself ?

Thanks,

Are you sure? It should be part of a standard Ubuntu install.

What do these commands return

```
uname -a
```

```
cat /etc/lsb-release
```

```
file apt-get
```  ```
ls -l /usr/bin/apt-get
``` and ```
dpkg -l apt
```
```
echo $PATH
```

If you do need to install it then.. 

Install the apt package from a CD/USB or use wget to retreive it (and any depencencies) and install the deb files.

Kind regards

---

### Post by shankarvalleru on 2012-02-08
FYI:

```

# uname -a
Linux testlinkdb01oak.jeeves.ask.info 2.6.9-42.ELsmp #1 SMP Wed Jul 12 23:27:17 EDT 2006 i686 i686 i386 GNU/Linux

# cat /etc/lsb-release
cat: /etc/lsb-release: No such file or directory

# file apt-get
apt-get: cannot open (apt-get)

# ls -l /usr/bin/apt-get
ls: /usr/bin/apt-get: No such file or directory

# dpkg -l apt
bash: dpkg: command not found

# echo $PATH
/home/jre1.6.0_22/bin:/usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/X11R6/bin



```

---

### Post by lisati on 2012-02-08
What version of Ubuntu are you running, and how are you running it?

---

### Post by shankarvalleru on 2012-02-08
Its not ubuntu, Its Cent OS. .!

---

### Post by Rafterman414 on 2012-02-08
CentOS uses yum. So it would be 

```
yum install gcc
```to install gcc for example. 

Ubuntu and CentOS/RHEL use different package managers. Ubuntu uses .deb (Debian Packages) and CentOS uses .rpm (Red Hat Package Manager)

Also you should have placed this in the other distro section of the forums instead of the Ubuntu section. It gets confusing.

---

### Post by lisati on 2012-02-08
> **shankarvalleru said:**
> Its not ubuntu, Its Cent OS. .!
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by lisati on 2012-02-08
I've moved your thread to "Other OS/distro talk" and added the "Centos" tag, so other users of the forums don't get confused.

---

