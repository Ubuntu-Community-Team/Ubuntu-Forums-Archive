---
title: "Readme help"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Gummi_ellahi on 2007-02-20
i have downloaded and extracted the rt2500 driver for my wireless belkin card. it needs to be compiled and installed.  i have located the readme file and it says:

For 2.6 series kernel:
a.  $make -C /path/to/source SUBDIRS=$PWD modules
    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.

b.  run '/sbin/insmod rt2500.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up' 

can someone explain what this means to me?
 is this what i type from the terminal? where would i find the configured and built kernel?
im running ubuntu 6.10 and am new to linux. also in the b step do i have to type in an Ip or YOUR_IP?

any help would be gratefully accepted.

---

### Post by Gummi_ellahi on 2007-02-20
anyone?

---

### Post by charles.g.moore on 2007-02-20
Where did you download the drivers from?

Have you compiled them yet?

I'm not exactly sure but whenever I d-load a driver I do a:
cd /*directory where i d-loaded it*
tar -xvzf *name of file*
ls
cd *into newly made directory*
sudo ./configure
sudo make
sudo make install

---

### Post by Gummi_ellahi on 2007-02-20
it says the ./configure command does not exist

there is a configure file but it wont let me run it

what i really need to know is what the readme file means. where should i have extracted the driver folder to?

---

### Post by Gummi_ellahi on 2007-02-20
is this something noone can help me with- is it lack of info? if so i can elaborate where required.

i know its a bit difficult but any small pointers would be helpful i will slowly figure it out.

---

### Post by annda on 2007-02-20
hi!

first off, compiling can be tricky.

it would be nice if you could tell us where you downloaded the driver from - the context would really help us help you.

do you have the buid-essential package installed?

what is the exact error message when you try to run ./configure (from the directory it's in)?

---

