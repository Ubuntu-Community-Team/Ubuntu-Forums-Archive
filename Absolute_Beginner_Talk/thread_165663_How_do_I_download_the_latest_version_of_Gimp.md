---
title: "How do I download the latest version of Gimp?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Linuxnewbie2006 on 2006-04-24
I'm new to Linux and Ubuntu. It's all new to me so if you guys can dumb it down for me I would appreciate it. 
I've removed Gimp 2.2.8 by using the Synaptic Package Manager but I can't figure out how to download the Gimp 2.2.11. 
:confused: I don't understand what I'm supposed to download or how to load it on the computer.
Can anyone help me??

---

### Post by nalmeth on 2006-04-25
Do have a package you've downloaded for it?
If you can find a .deb file, it would be easiest and best.
Next best would be an .rpm file or a .gz file
Post back when you find a package for the new GIMP

---

### Post by Linuxnewbie2006 on 2006-04-25
[QUOTE=nalmeth]Do have a package you've downloaded for it?
If you can find a .deb file, it would be easiest and best.
Next best would be an .rpm file or a .gz file
Post back when you find a package for the new GIMP[/QUOTE]


I have downloaded this: /Desktop/gimp_2.2.10-2_i386.deb

Thanks for your help.

---

### Post by nalmeth on 2006-04-25
I don't remember if gdebui is installed on breezy, or if it was made available. This is what allows you to double click on a .deb to install it.
I will assume it isn't available.
ok, open up a terminal (APPLICATIONS --> ACCESSORIES --> TERMINAL)
```
cd Desktop
sudo dpkg -i gimp_2.2.10-2_i386.deb
```

And you should have the new GIMP!

---

### Post by Linuxnewbie2006 on 2006-04-25
when I type in the second line i get "command not found"

---

### Post by nalmeth on 2006-04-25
thats.. odd..
does it say which command is not found? sudo or dpkg?
neither would make sense, since both are included with ubuntu
sudo gives you admin priviledges to perform system duties like installing/uninstalling apps
dpkg is how the package manager installs the applications.
try:
sudo apt-get update
sudo apt-get upgrade
this will update all the available packages on your system, and show us that sudo is working fine.
then try
sudo dpkg -i gimp_2.2.10-2_i386.deb
again..
sorry, but really I'm at a loss as to why you would get command not found, unless you typed it in incorrectly.
Please post again with your results

---

### Post by meborc on 2006-04-25
[QUOTE=Linuxnewbie2006]when I type in the second line i get "command not found"[/QUOTE]
may be the file is not found... where did you download the gimp file? if it is on your desktop then nalmeth's instructions are OK... if it is somewhere else, in some sub-folder then you need to navigate to that folder before issuing the dpkg command...

---

### Post by Linuxnewbie2006 on 2006-04-25
I tried again, I must have done something wrong...now I'm getting that the I need that the "operation requires superuser privilage"

---

### Post by mostwanted on 2006-04-25
[QUOTE=Linuxnewbie2006]I tried again, I must have done something wrong...now I'm getting that the I need that the "operation requires superuser privilage"[/QUOTE]

Remember typing sudo.

---

### Post by Linuxnewbie2006 on 2006-04-25
Ok I'm getting closer but now I get...

Unpacking gimp (from gimp_2.2.10-2_i386.deb) ...
dpkg: dependency problems prevent configuration of gimp:
 gimp depends on gimp-data (= 2.2.10-2); however:
  Version of gimp-data on system is 2.2.8-2ubuntu6.
 gimp depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.
 gimp depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 gimp depends on libpango1.0-0 (>= 1.10.2); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 gimp depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing gimp (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimp

How do I download the required programs?

---

### Post by Jagot on 2006-04-25
I'm not entirely sure it'll work but you could try:

sudo apt-get -f install

---

### Post by picpak on 2006-04-25
This is what I did to get Gimp 2.2.10:

Open up a terminal and put (one line at a time):

wget [http://backports.org/debian/pool/main/g/gimp/gimp_2.2.10-1bpo1_i386.deb](http://backports.org/debian/pool/main/g/gimp/gimp_2.2.10-1bpo1_i386.deb)

wget [http://backports.org/debian/pool/main/g/gimp/libgimp2.0_2.2.10-1bpo1_i386.deb](http://backports.org/debian/pool/main/g/gimp/libgimp2.0_2.2.10-1bpo1_i386.deb)

wget [http://backports.org/debian/pool/main/g/gimp/gimp-data_2.2.10-1bpo1_all.deb](http://backports.org/debian/pool/main/g/gimp/gimp-data_2.2.10-1bpo1_all.deb)

wget [http://ftp.us.debian.org/debian/pool/main/libe/libexif/libexif10_0.6.9-6_i386.deb](http://ftp.us.debian.org/debian/pool/main/libe/libexif/libexif10_0.6.9-6_i386.deb)

sudo dpkg -i *.deb

---

### Post by bernardfrancois on 2006-05-05
Make sure you do this in a directory without that doesn't already have .deb files (or just create a new directory, then 'cd' to that directory and execute the commands above).

---

