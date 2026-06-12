---
title: "vnc remote"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by therob1 on 2007-08-09
Hi, ive tried using KRFB (kde desktop sharing) so we can connect to the linux box from our windows clients, however we are finding the program quite poor and randomly drops connection. Having gone straight to realvnc themselves there is the option of an RPM file and a tar.gz.

i tried to use the rpm file at first and the assocaited program stated that it couldnt open the file?  having tried the other it showed me what appeared to be a zipped formatted file and i tried extracting the files but then didnt know what to do with them?

could someone pleae enlighten me what to do here, I come from a windows environment which im just used to exe and setup files...:confused:

anyone recommend a better program to use for us to connect to this box with?

---

### Post by splintercellguy on 2007-08-09
Install alien to convert RPM to DEB:

sudo apt-get install alien

then do:

sudo alien -k <name of RPM>

then do

sudo dpkg -i the name of the DEB

---

### Post by wirelessmonkey on 2007-08-09
Open your terminal, cd to the directory of the .tar.gz file

then:
tar xvfz nameoffile.tar.gz
cd nameoffile
./configure
make
sudo make install

---

### Post by therob1 on 2007-08-09
thanks for that i will give it a try.

do you know how or why there are all these different formats, from a new user point of view its quite confusing:confused:

---

### Post by therob1 on 2007-08-10
> **splintercellguy said:**
> Install alien to convert RPM to DEB:

sudo apt-get install alien

then do:

sudo alien -k <name of RPM>

then do

sudo dpkg -i the name of the DEB

I'm now getting the error message saying xvncviewer conflicts with vnc (version 4.1.2.1) is to be installed.

then basically says its not going to install it. i've tried looking in the add and remove programs and cant see to find this xvncviewer to try and remove it , any ideas?

---

