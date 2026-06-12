---
title: "Make Library setup error"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by DevyD on 2006-01-18
Hi there

I'm trying to install the "make_3.80-9_i386.deb" in the command line using the "apt-get install make_3.80-9_i386.deb" command, it reads the package list and then builds the dependancy tree successfully, but then it brings back the error that it could not find the error.

Can anyone please tell me why it would give this error and how to solve it? I am sure that this is the correct package that I am trying to install.


Thanks.

---

### Post by gord on 2006-01-18
if you have the actual .deb file on your hard disk, the command you need to perform is (assuming you are in the directory the .deb file is in)
```
sudo dpkg -i make_3.80-9_i386.deb
```

---

### Post by mcduck on 2006-01-18
apt-get is for installing from internet repositories. To install a .deb package you downloaded yourself, you need to use 'sudo dpkg -i /path/to/your/package.deb'

So if the package is in your desktop, 'sudo dpkg -i ~/Desktop/make_3.80-9_i386.deb'.

edit: by the way, make 3.80-9 is in the repositories, so you could just 'sudo apt-get install make', or if you are trying to compile something, 'sudo apt-get install build-essential' to get make and everything else needed for compiling. I'd suggest also installing checkinstall, and then instead of running 'sudo make install' using 'sudo checkinstall' so that you can easily uninstall programs you compiled yourself. (checkinstall will create a -deb and install that)

Have a look at this too: [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by DevyD on 2006-01-18
Thanks for the help, it worked!!!

---

