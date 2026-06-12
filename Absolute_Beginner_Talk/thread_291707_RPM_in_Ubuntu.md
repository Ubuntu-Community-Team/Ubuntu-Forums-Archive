---
title: "RPM in Ubuntu"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by grimsanta on 2006-11-02
I'm brand new to linux, and therefore Ubuntu and so I need some help.  I've figured out a few things, and have successfully installed make, and alien.

My goal here is to install limewire, but to do that, alien is telling me that i need rpm or something.

When I type in "alien LimeWireLinux.rpm", it returns to me with "sh: rpm: command not found"

So i've been told I need to install RPM.

A few things...

1. Where can i get RPM?  I've searched with no luck
2. How do I install it?

---

### Post by %hMa@?b&lt;C on 2006-11-02
first you need to install alien 
sudo aptitude install alien
then to alien the rpm, cd to teh directory witht the rpm in it
sudo alien -i Lime*.rpm

p   apt-rpm-repository              - tools to create an APT RPM repository
p   libapt-rpm-pkg-dev              - development files for APT for RPM library
p   libapt-rpm-pkg-libc6.3-6-0      - APT for RPM library
p   librpm-dev                      - RPM shared library, development kit
v   librpm0-dev                     -
i   librpm4                         - RPM shared library
p   lsb-rpm                         - Red Hat package manager for LSB package bup   python2.4-rpm                   - Python bindings for RPM
i   rpm                             - Red Hat package manager
p   rpm2html                        - Generate HTML index from directories of RP

those are rpm packages i have the ones marked with an i i can install rpms iwth my current setup

---

### Post by taurus on 2006-11-02
```

alien <filename>.rpm
sudo dpkg -i <filename>.deb

```
However, why not use frostwire since it's a open source and it looks and feels exactly like LimeWire.  And besides, there is a .deb version for Ubuntu!!!

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by grimsanta on 2006-11-02
what is sudo?

---

### Post by grimsanta on 2006-11-02
Yeah, that doesn't work, when i put alien -i LimeWireLinux.rpm it says sh: rpm: command not found

Alien is installed.

---

### Post by Fully216 on 2006-11-02
For future reference, you might find this site helpful.  Cheers,

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by slimdog360 on 2006-11-02
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
it gives you temporary root privilges

---

### Post by Fully216 on 2006-11-02
sudo allows a command to be executed in the terminal with root privileges.

I just installed the debian package.  I would try that.  After you have downloaded the package, simply type the following:

sudo dpkg -i FrostWire-4.10.9-2.i586.deb

---

### Post by grimsanta on 2006-11-02
I installed it, but i see no icon, how do i start it?

---

### Post by taurus on 2006-11-02
You don't see an icon in Applications -> Internet???

---

### Post by grimsanta on 2006-11-02
I see it now, but it doesn't do anything when i double click it, nothing at all.  My icon doesn't even change to the loader.

---

### Post by Fully216 on 2006-11-02
Hmmm, mine appeared in applications > internet.

you can always type forstwire in a terminal to start the program.

---

### Post by Fully216 on 2006-11-02
I think you need to have java installed as well.

---

### Post by taurus on 2006-11-02
Of course you need to install java and get it working first before you can use limewire or frostwire.  Why don't you use Automatix2 and install java on your machine first.  You can get more detail about how to install automatix2 at [http://www.getautomatix.com/](http://www.getautomatix.com/).

---

