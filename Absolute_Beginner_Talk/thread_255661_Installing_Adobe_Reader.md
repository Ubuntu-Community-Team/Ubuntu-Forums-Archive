---
title: "Installing Adobe Reader"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by kq6up on 2006-09-11
I get the message:

'Adobe Reader' is not available in any software channel.The application might not support your system architecture.

I have all of the software repositories uncomented.  Help!

Here is my 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by orb9220 on 2006-09-11
There is already a pdf reader by default called evince.

---

### Post by Najand on 2006-09-11
open a terminal and use this command:
```

sudo apt-get update && sudo apt-get upgrade

```

Then try to install it using 
```

sudo apt-get install acroread

```

---

### Post by Linux Lover on 2006-09-11
What I did is :

Downloaded latest AdobeReader from [http://www.adobe.com/products/acrobat/readstep2.html]("http://www.adobe.com/products/acrobat/readstep2.html")

Selected .tar file in the selection list.

Placed in /usr/local/bin

$ sudo tar -xvzf AdobeReader_enu-7.0.8-1.i386.tar.gz
$ cd AdobeReader
$ sudo ./INSTALL

Now you please make sure :
The installation directory do not exist. You will be prompted to create the installation directory during installation. Please respond `yes' in the appropriate place.

In the installation process you will be asked with, "Do you want to install browser plugin? [y/n]" -- press `y' here (if u need it)

Respond with `y' in the place where you are being asked "Do you want to perform automatic installation? [y/n]"

For firefox's plugin directory, you have to provide the firefox path as `/usr/lib/firefox' put it in the right place.

At last you will be prompted with "Finished automatic install. Do you want to perform manual install? [y/n]"
Press y, if you have more browsers and you want to use AdobeReader as plugin for those too. To do so, you will need to put the plugin directory same as above, otherwise put `n' and the installation will be finished.

---

### Post by Najand on 2006-09-11
When an Ubuntu Repository is available please try to use them, because they are already compiled for Ubuntu and chance of failure in Installation is the lowest. So try using apt-get, aptitude or synaptic to install it and if you were unseccessful use the .tar package in the Adobe Site.

---

