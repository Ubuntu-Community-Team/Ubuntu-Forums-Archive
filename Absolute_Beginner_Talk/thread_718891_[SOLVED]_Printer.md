---
title: "[SOLVED] Printer"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ProgenitorVirus on 2008-03-08
Adding a networked printer available on a Windows network; Ubuntu finds it fine, but when given the choice to install the listed drivers, the only one around my model is Samsung ML-2550.  Fine and dandy, but the printer I'm using is an ML-2510.  So, I go to Samsung.com and download me the "Unified Printer Driver".  And from here, is where I'm lost.  Being a Windows user up until now, I have no idea how to compile an installer, or install the driver, I'm used to the .exe native to Windows.  But here, I'm totally lost.  I extract the file, to get a folder called "cdroot".  Inside, is a file called "autorun" and a folder called "Linux" which has folders named by computer architectures, and files called like "install.sh" and "check_installation.sh".

So, I guess my question is, how do I install the driver?

Thanks!

---

### Post by cotcot on 2008-03-08
What is the extension of the file you downloaded ?
Search for a text file README or INSTALL. There you probably will find how to install.
The default is (after you have installed build-essential with synaptic) 

cd to-the-folder-you-extracted
./configure
make
sudo make install

---

### Post by ProgenitorVirus on 2008-03-08
It was in .tar.gz

I extracted it, and cant find any README or INSTALL :S

---

### Post by ProgenitorVirus on 2008-03-08
Also, when using the ./configure command, it returns an error "bash: ./configure: No such file or directory"

---

### Post by kwacka on 2008-03-08
Hope this helps: [http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2550](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-2550)

- set up as a standard ps printer, using the Samsung ppd file.

---

### Post by ProgenitorVirus on 2008-03-08
Thanks kwacka!  Worked perfectly!

---

