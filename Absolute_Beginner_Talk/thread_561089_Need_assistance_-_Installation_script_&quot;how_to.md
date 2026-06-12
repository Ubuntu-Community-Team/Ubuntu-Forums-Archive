---
title: "Need assistance - Installation script &quot;how to&quot;"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by rhardie on 2007-09-27
This is going to be two questions:

1. I attempt to move a file to a folder such as Apache2.  I am looking for the correct use of the make or move directory commands.

2. How do I execute the installation scripts of a software package?  I'm pretty new at this stuff.

The zipped file is on my desk top, I unzipped it and have found the installation script.

Do I cut and past the script into the command line editor?

---

### Post by hyper_ch on 2007-09-27
(1) You mean by a gui or by the terminal?

(2) What is that software package?

---

### Post by rhardie on 2007-09-27
Let us suppose I am wanting to install Joomla on my Ubuntu server using the terminal.

---

### Post by hyper_ch on 2007-09-27
do you have apache / php / mysql running?

---

### Post by madoracle on 2007-09-27
> 1. I attempt to move a file to a folder such as Apache2.  I am looking for the correct use of the make or move directory commands.

cp <file> <destination> 

> 2. How do I execute the installation scripts of a software package??  

I assume you have a package with an INSTALL or INSTALL.SH file. From the terminal, generally, go into the uncompressed folder and type:

./configure
make
sudo make install

If its a .deb package you type

dpkg install packagename (I think, normally I apt-get any .deb package)

Edit: Some packages require other commands to install. Look thru the folder for a file marked README or INSTALL and if you are in terminal vi <Filename> generally it will give step by step instructions for installation.

---

