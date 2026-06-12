---
title: "bunzip?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-04-19
my goal is to get joomla installed on ubuntu server 7.10 using the cli..

I think i have downloaded the .tar.bz2 package of joomla. I only think that because i havent ever downloaded anything with linux before. At my command prompt i can type the command ls and the filename Joomla_1.5.2-Stable-Full_package.tar.bz2 appears in red letters. Is this a good thing?

Yesterday i was told to bunzip this file but, when I type in (with or without sudo) bunzip Joomla_1.5.2-Stable-Full_package.tar.bz2  
at the command prompt, i recceive the following:

-bash: bunzip: command not found

Did i succcessfully download joomla and if so, how do I unzip the current package?

---

### Post by Frequent Modulation on 2008-04-19
i attempted to install bunzip (is this a software package?) with the following:

sudo apt-get install bunzip

got the following:

E: Couldn't find package bunzip

how do i go about getting in a position to use bunzip or any unzip program to unzup this .tar.bz2 package?

---

### Post by Can+~ on 2008-04-19
Wikipedia has information of it:

[http://en.wikipedia.org/wiki/Bzip2](http://en.wikipedia.org/wiki/Bzip2)

bunzip2

---

### Post by enigmaniac23 on 2008-04-19
The command you need is actually bunzip2, not just bunzip

Since it's also a tar, I think you can do :

tar -xjvf Joomla_1.5.2-Stable-Full_package.tar.bz2 

for just a bz2 you can:

bunzip2 filename.bz2

---

### Post by Frequent Modulation on 2008-04-19
sweet... got it unzipped and unpacked. on to how to read the install.php file...  

hehe

thanks guys

---

### Post by Frequent Modulation on 2008-04-19
cat  :)

---

