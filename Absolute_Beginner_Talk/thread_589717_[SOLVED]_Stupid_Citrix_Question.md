---
title: "[SOLVED] Stupid Citrix Question"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by anchor1te on 2007-10-24
Just installed Gutsy.  Was able to use VNC and RDP.  ICA seems to be greyed out.  I'm assuming I need to install Citrix, or am I overlooking something?

Thanks!

---

### Post by usererror on 2007-10-24
whoa, what do you mean?  To do Citrix where I am...I install the ICA Client from Citrix's web site and then click the links in our 'citrix portal'.  Maybe you guys have a different setup?

---

### Post by usererror on 2007-10-24
whoa, what do you mean?  To do Citrix where I am...I install the ICA Client from Citrix's web site and then click the links in our 'citrix portal'.  Maybe you guys have a different setup?

Oh, just looked at my terminal server, and ICA is not blocked out on mine, but maybe it is because I have the ICA client installed.

---

### Post by anchor1te on 2007-10-24
That's what I thought.  It's set up to be utilized, but needs to be installed.  Time to head to the Citrix website.

Thanks!

---

### Post by lilnovina on 2007-10-24
You are correct. You need to install the ICA client for Linux. The setup is a bit tricky or at least was for me, so I created a document for the process. Just follow these steps and you shouldn't have any trouble!

First, obtain the Citrix ICA Client tarball by going to [http://www.citrix.com/](http://www.citrix.com/) and selecting "Downloads". Or if you specifically want the current Linux x86 tarball, go to [http://download2.citrix.com/files/de/products/client/ica/current/linuxx86.tar.gz](http://download2.citrix.com/files/de/products/client/ica/current/linuxx86.tar.gz). From this point on in the documentation, the tarball will be assumed to be the x86 version, so substitute accordingly if you have to.



Once you've obtained the tarball, you need to unpack it. Pick a temporary location to unpack this tarball. For this page, we’ll use /tmp/citrix/. So create the temporary directory, move the tarball to that directory and change into that directory:



 



1. mkdir /tmp/citrix/



 



2. mv linuxx86.tar.gz /tmp/citrix/



 



3. cd /tmp/citrix/







Now to run the installation command you must run the install as root. Execute the installation script, and follow the instructions as prompted. From a terminal window:



 



4) sudo ./setupwfc



 



 



After setup you will need to install some libraries. Do this :



 



sudo apt-get install libmotif3







All set to go. Start the program by navigating to the install dir and tying:



 



5) ./wfcmgr

Once it launches you should be in familiar territory and can create your ICA connections or the published app of your choice.

---

### Post by anchor1te on 2007-10-24
Awesome!  Thanks for the steps.

---

