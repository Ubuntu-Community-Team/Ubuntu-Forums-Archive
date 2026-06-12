---
title: "Gimp install problem"
date: 2012-04-27
forum: Art &amp; Design
---

### Post by safetygary on 2012-04-27
Error received when attempting gimp install from software center. Any help greatly appreciated. 

The following packages have unmet dependencies:

gimp: Depends: python-gtk2 (>= 2.8.0) but 2.24.0-3 is to be installed
      Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu9 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed


      Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.10-0ubuntu6 is to be installed
      Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.36.1-0ubuntu1 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
      Depends: python (>= 2.7.1-0ubuntu2) but 2.7.3-0ubuntu2 is to be installed

---

### Post by vVvSHADOWvVv on 2012-05-03
The solution to this problem is to remove the PPA for GIMP 2.8.

I had attempted to install the new version of GIMP by the following procedure:
sudo add-apt-repository ppa:otto-kesselgulasch/gimp sudo apt-get update sudo apt-get install gimp

If you do this with the older version of GIMP installed it will break
your installation.

To fix this, you must remove the PPA with 
sudo add-apt-repository --remove ppa:otto-kesselgulasch/gimp

Then run: 
sudo apt-get update
sudo apt-get install -f


Then be sure GIMP is no longer installed by running apt-get remove gimp

Now you must update apt again

Then re-add the PPA and install GIMP. This will install the newer version
of GIMP for you without the DEP errors.

Let me know 

&#7780;&#11367;&#480;&#7430;&#336;&#412;

---

### Post by safetygary on 2012-05-05
Thank you very much however, I tried the above and received the following:

xxxx@xxxx-Latitude-D810:~$ sudo add-apt-repository --remove ppa:otto-kesselgulasch/gimp

You are about to remove the following PPA from your system:
 CAUTION!

This PPA could break your installed OS. There are dependency issues especially for Oneiric (11.10). Only use it if you know what you do! I'm working with others on a stable and reliable solution.

Regards
 More info: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main' doesn't exist in a sourcelist file
Error: 'deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main' doesn't exist in a sourcelist file

Any other possibilities?

---

### Post by vVvSHADOWvVv on 2012-05-05
> **safetygary said:**
> Thank you very much however, I tried the above and received the following:

xxxx@xxxx-Latitude-D810:~$ sudo add-apt-repository --remove ppa:otto-kesselgulasch/gimp

You are about to remove the following PPA from your system:
 CAUTION!

This PPA could break your installed OS. There are dependency issues especially for Oneiric (11.10). Only use it if you know what you do! I'm working with others on a stable and reliable solution.

Regards
 More info: [https://launchpad.net/~otto-kesselgulasch/+archive/gimp]("https://launchpad.net/%7Eotto-kesselgulasch/+archive/gimp")
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main' doesn't exist in a sourcelist file
Error: 'deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main' doesn't exist in a sourcelist file

Any other possibilities?


 sudo apt-get purge Gimp*  then run the -f then re-add the PPA

---

### Post by safetygary on 2012-05-05
Perfect - thanks for helping a newbie!!!

---

### Post by vVvSHADOWvVv on 2012-05-05
No prob 
shadowsgovernment.com

---

