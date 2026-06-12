---
title: "help.."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by pixelized on 2007-06-25
now i installed all the tarballs i downloaded what and where do i compile them and how?i read the read me..

---

### Post by w4ett on 2007-06-25
I found this helpful in the past:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by kevdog on 2007-06-25
If you are new just to correct your terminology.  You download tarballs and extract them (either unzip, untar).  Within the extracted files you need to compile and install.  Usually you do not "install" tarballs.

To compile you will need the build-essential package.  The usual (but this sometimes varies between what is being installed) process to compile, install from source is
make
sudo make install

Sometimes there is a file in the extracted files called INSTALL or README that will help you with the above commands (ie ./configure).

Post back if you have problems.

---

### Post by jml on 2007-06-25
I'm curious why you are installing software via tar balls?  That is probly the most tedious and difficult way to install applications in my opinion.  I find that once I enable the Universe and Multiverse repositories, plus the restricted format repository I can find what I want and let Synaptic install it for me.  That way I don't have to manually deal with dependancies.  Are the applications you want to install not available in the repositories?  I'm not trying to be critcal, and mastering tar balls and manual installation is a good learning experience, but package managers like Synaptic can make your life so much easier.

Joe

---

