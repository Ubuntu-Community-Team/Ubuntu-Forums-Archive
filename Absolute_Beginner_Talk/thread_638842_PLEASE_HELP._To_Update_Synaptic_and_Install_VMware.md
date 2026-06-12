---
title: "PLEASE HELP. To Update Synaptic and Install VMware"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by nutpuk on 2007-12-12
Hi all,

This is my first post and I'm in need of help.

I'm running Ubuntu 7.10 and have two problems

There both related.

I'm wanting install VMware on my machine but Synaptic doesn't list it anywhere. I'm wondering what code I need to enter in a shell to update Synaptic and the packages and download more so I can install VMware?

second

As I can't install VMWare via synaptic I have downloaded VMware 1.0.4 to my desktop but it is a tar.gz file.

Could someone please be kind enough to tell me the code in a shell to browse to the desktop, unpack it and install it.

I'm new to linux and I'm struggling 

Please help me

Thanks

---

### Post by nutpuk on 2007-12-12
Anyone Please

---

### Post by DeLaNooch on 2007-12-12
Afraid I can't help you with the first part, but to navigate to your desktop and unpack your tarball, do as follows (this is assuming your tarball is named "vmware.tar.gz," replace this with the actual name of the file):

> 
cd Desktop
tar -xf vmware.tar.gz


OR If you are more graphically inclined, just right-click on the tarball and select "Extract Here."

That will unpack it to your desktop.  If you now see a *.deb file on your desktop, run it by double-clicking it or entering the following in the terminal (you will need to enter your password either way) :

> sudo vmware.deb


If the unpacked contents is within a directory, you will have to navigate to that directory before you can run it.

I am also new to linux.  I have used it here and there in the past but this is the first time I am attempting to use it as my sole OS.  I know just enough commands to be dangerous! :lol:

---

### Post by tighem on 2007-12-12
VMWare is pretty simple to install.

After it's extracted, you will need to run the install script as root:

sudo ./vmware-install.sh

Answer all questions with the defaults and you should be good to go. You will need to get a Serial Number from vmware to answer the last question.

---

