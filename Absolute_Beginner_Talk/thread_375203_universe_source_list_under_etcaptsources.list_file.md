---
title: "universe source list under /etc/apt/sources.list file?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-03-03
Hello,

I want to use gnucash. When i install it trough automatix it only installs an old version 1.8 or something whereas they have 2.0.5 already. Now I found this ([http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html](http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html)) page, where it first says that I need to check my "universe source list under /etc/apt/sources.list file" after which I need to do "sudo apt-get install gnucash". 

If I just immediatly do the "sudo apt-get install gnucash" it just installs the 1.8 version.

What is that list they are talking about and what do I need to do to it?

---

### Post by taurus on 2007-03-03
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by kramer65 on 2007-03-03
Thanks, but when I do that, and then do "sudo apt-get install gnucash" i still get gnucash 1.8.12

Through automatix I get the same. Is there another way how I can get up to date with the installation of gnucash? I downloaded the gnucash-2.0.5.tar.gz file. But how would I go over installing that?

---

### Post by taurus on 2007-03-03
If the latest version is not in the repos, then you can either download the .deb is there is one or build it from the source yourself.

Look at Section 4.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by kramer65 on 2007-03-03
ok thanks. (learning point again.. :-) )

But this now runs me into a problem.. everything seems to go ok until I get this: 'make: *** No rule to make target `install'.  Stop."

And everything stops...

I did install build-essential in synaptic.

Any idea how this is possible?

---

### Post by taurus on 2007-03-03
Did you remember to run "**./configure**" first before you ran "**make**"?

---

### Post by kramer65 on 2007-03-03
I did this (saved it.. :))

tar -xvzf gnucash-2.0.5.tar.gz
cd gnucash-2.0.5
./configure
make
sudo checkinstall -D

---

### Post by taurus on 2007-03-03
Are there any error messages at the end after you ran ./configure?

---

### Post by kramer65 on 2007-03-03
Yes.. It says this:

checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool
ricam@ricom:~/Desktop/gnucash-2.0.5$ make
make: *** No targets specified and no makefile found.  Stop.

---

