---
title: "A new challenge"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by martinja on 2007-11-22
I have a keen interest in setting up a server and becoming familiar with client side applications (namely Apache, MySQL, PHP). I have decided to install Ubuntu 7.10 Server Edition on a Compaq Desktop Pro EN, P3 660 MHz and 254 RAM. It has two harddrives, the bootable drive has 9 GB and there is a secondary drive with 35GB. I gather the server edition comes with the clientside applications that I want to use?
I am new to Linux and it will be a steep learning curve. I gather it also has a optional GUI to use, at least to begin with? Does this all sound feasible? Is the 9GB drive large enough? How will I be able to use the larger35GB drive; To store files, applications (my previous experience was with Windows 2000)? 
Are my assumptions correct and is there any helpful advice that anyone could give me?
Thanks for your consideration.
Julie

---

### Post by delphiguy on 2007-11-22
I am not an expert but here goes.

The nice thing about linux is that whether it says desktop or server, it is still
a server os.  what I would do is install Ubuntu/Kubuntu and then install 
Apache, mySQL, PHP this way I can also install the GUI frontends for them also.

As for the 35GB drive, yes you can use it.  I have a smilar machine to
yours and I have 3 HardDrive in there, 1x40GB(Boot/Root), 2x120GB(My
Files), what I do is I just mount my 120GB to be on /MyFiles, /MyFiles2.

You can mount them by doing something like this:
sudo mount /dev/sda1/ /MyFiles 

of course the directory /MyFiles must exist first.  Or if you want to have
that drive mounted to /MyFiles everytime you boot you can edit /etc/fstab
and add this line:
/dev/sda1 /MyFiles ext3 defaults 0 0

Hope this helps.

---

