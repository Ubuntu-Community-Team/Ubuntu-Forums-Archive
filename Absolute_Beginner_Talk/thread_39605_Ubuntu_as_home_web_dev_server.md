---
title: "Ubuntu as home web dev server?"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by nathanpitman on 2005-06-05
Hi, I am totally new to linux and ubuntu. I have recently gotten hold of an old Dell box to run as a home based web dev server as much of my daily work is PHP/MySQL.

I initially downloaded and installed a copy of Debian Woody but have been finding it hard work in terms of configuration and wonder whether ubuntu would be an easier option.

I have a question... would ubuntu seem a good choice for me...? Is ubuntu easy to set up for access over a windows workgroup... and... does ubuntu support linksys qireless network cards?

---

### Post by GrumpySimon on 2005-06-05
I use it for web dev all the time. I compiled and installed the components myself (PHP4, Apache2, MySQL 4.1, mod_python, etc) , but it's much easier to just use apt to install everything for you. 

What exact problems did you have with Woody?

--Simon

---

### Post by Mez on 2005-06-05
Configurations much easier with ubuntu... just install apcahe and the PHP modules through synaptic, install a couple of other things and voila :D done :D

Only thing I had to do was edit the config so that it had an addtype for php (well i uncommented the current ones) and all was well

---

### Post by Gtaylor on 2005-06-05
I too use Ubuntu in my daily activities for work even though my pages are eventually moved to a SuSe Enterprise box for active use. I would strongly recommend Debian/Ubuntu for a personal playground as the number and quality of the webserver related packages is staggering.

---

### Post by artastic on 2005-06-07
This looks like a decent place for my question.  I want to set up a spare pc (with Ubuntu) for web dev. The problem is it'll be a while before I can connect it to web, so I can't use the apt-get command to get what I need.  

Is there an easy way to get and install packages if you have to physically transfer them from a windows computer using memory stick etc.

Bare in mind I'm a complete amateur and wouldn't know how to compile anything.

---

### Post by wylfing on 2005-06-07
You should not need to compile anything. (Don't be ashamed of that -- I am kind of an old hand with Linux and I also avoid compiling from source.) If you have the Ubuntu installation CD, you can install some things from there. Try running synaptic and see what you can select for installation. I am pretty sure apache is on the CD, but I don't think PHP is.

It is technically possible to download packages onto a Windows machine and copy them over, but package dependencies can make this problematic. Why don't you say what software (other than apache) you require?

---

### Post by artastic on 2005-06-07
checked out synaptic and I think all i need is php. already downloaded .deb package but not sure how to install it.

---

### Post by wylfing on 2005-06-08
The command to install a package is:
```
dpkg -i filename
``` 
Where 'filename' is the name of the package file.

However, installing packages is a little different than installing a program on Windows. The file you downloaded (which probably looks like php4_4.3.10-15_all.deb) "depends" on other packages. So in order to install php4_4.3.10-15_all.deb, you must also install packages like libapache2-mod-php4_4.3.10-15_i386.deb. But that package depends on other packages too.

This is what we (not so) affectionately call "dependency hell." The true list of packages you need to download and install could be quite extensive. In order to handle all this complexity, we use the 'apt-get' command, which handles finding and installing all the necessary dependencies for us. However, since you can't use that method because of your lack of net connection, you'll have to track down and install packages manually. It is going to be kind of tedious.

So...run the 'dpkg -i' command on the file you downloaded. It will report that the package you are trying to install depends on some other  packages. Now that you've got the names of them, go download them and run the 'dpkg -i' command on *those* files. Once again, it may tell you that what you are trying to install depends on other packages. Keep repeating this process until you have installed all the necessary packages. With luck, the list of packages will be fairly short (perhaps only 3). With bad luck, it's going to be long.

One more thing: you may have a choice between installing libapache-mod-php4 or libapache2-mod-php4. I'm betting you installed apache 2.0, so you should choose libapache2-mod-php4.

HTH

---

### Post by artastic on 2005-06-09
[QUOTE=wylfing]The command to install a package is:
```
dpkg -i filename
``` 
Where 'filename' is the name of the package file.

[/QUOTE]

Cool thanks for the help, now I've got apache php flash player all working.

packages.ubuntu.com lists all the dependencies for easy downloading so that was relatively painless.

still having problems with trying to install 'mysql-server' though.  It depends on perl (>= 5.8.4-1) which depends on perl-modules (>= 5.8.4-2ubuntu0.4) which depends on perl which depends on perl-modules add infinitum. arrghh

---

### Post by wylfing on 2005-06-09
[QUOTE=artastic]
packages.ubuntu.com lists all the dependencies for easy downloading so that was relatively painless.[/QUOTE]
Great! Very resourceful.

[QUOTE=artastic]
still having problems with trying to install 'mysql-server' though.  It depends on perl (>= 5.8.4-1) which depends on perl-modules (>= 5.8.4-2ubuntu0.4) which depends on perl which depends on perl-modules add infinitum. arrghh[/QUOTE]
Both perl and perl-modules are on the installation CD. Try using synaptic again.

---

### Post by poofyhairguy on 2005-06-09
[QUOTE=nathanpitman] does ubuntu support linksys qireless network cards?[/QUOTE]

Depends. Not all Linksys cards have the same chip in them. I have four WPC11 cards. The two version twos and the version three work great (they are really prism cards), but my version 4 only works with ndiswrapper (which is a pain to do so it never get used)-it is really a realtek card. My friend has two wpc54g cards. The version one (a broadcom card) doesn't work without ndiswrapper and never will. His version two card is plug and play. So it depends. But if it doesn't work out of the box, you have to use ndiswrapper. All Linux will be the same in this regard- no Linux has these drivers as they are not open.

---

