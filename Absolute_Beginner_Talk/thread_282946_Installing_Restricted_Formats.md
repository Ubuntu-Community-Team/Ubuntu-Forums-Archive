---
title: "Installing Restricted Formats"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-23
Hello! I have been trying to install the restricted formats. This is my terminal output:

```

amitroy5@Amit:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse xine-ui libxine-main1 libxine-extracodecs w32codecs libdvdread3 libdvdcss2 flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
  w32codecs: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages
amitroy5@Amit:~$

```

Also, I was using this Wiki article: [http://ubuntuforums.org/showthread.php?t=182902](http://ubuntuforums.org/showthread.php?t=182902)

How can I fix this? Thanks!

Also, here are my respitories:
```

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb [WWW] http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src [WWW] http://packages.freecontrib.org/plf edgy-plf free non-free

```

Thanks!

---

### Post by Fully216 on 2006-10-23
From what I understand, the libdvdread3 package must be installed before the libdvdcss2.  Now that you have it installed, try downloading the libdvdcss2 library by typing in a terminal (assuming you do not have an amd64 system):

sudo  /usr/share/doc/libdvdread3/examples/install-css.sh

You can download the w32codecs package from an unoffical repository and install it with dpkg, again assuming a non amd64 system:

      wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
      sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

---

### Post by Marsolin on 2006-10-23
The last repository the you have listed is for edgy and the others are dapper. That's why you get a conflict.

---

### Post by amitroy5 on 2006-10-23
Should I remove the following line then:

```
deb-src [WWW] http://packages.freecontrib.org/plf edgy-plf free non-free
``` ? Thanks!

---

### Post by Perfect Storm on 2006-10-23
Change all the edgy to dapper will be sufficient. (as you on Dapper ubuntu, edgy is the next release of Ubuntu(in a few days)).

---

### Post by TheWizzard on 2006-10-23
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
EDIT: never mind, see previous posts

---

### Post by amitroy5 on 2006-10-23
Does anyone have a good liest of repositories?

---

### Post by Perfect Storm on 2006-10-23
You can use this to set up your own: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

