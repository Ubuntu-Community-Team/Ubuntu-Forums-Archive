---
title: "Install tar.gz file problem"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by brett611 on 2008-01-21
I'm trying to install a tar.gz of k9copy with no luck.  I've looked at many posts (attached) and psychocats and the install instrux file that came with the tar.gz.  I'm trying to install this version b/c the one in Synaptics doesn't work for me.

Attached is the error details.  Assistance most appreciated.
Thanks!

---

### Post by Lostincyberspace on 2008-01-21
Are you running it as root if not then you should try that.

---

### Post by compiledkernel on 2008-01-21
first of all, do you have build-essential package? 

sudo apt-get install build-essential 

then 

tar zxvf nameoffile.tar.gz
cd ~/nameoffile
./configure
make

sudo -i (to become root) 

make install 

I just ran the source isntall for 1.2.2 versioning , and it compiled and installed ok for me.

---

### Post by brett611 on 2008-01-21
Thanks- I did not have this.  I installed it & got much further this time but still got an error.  After the "./configure" part it ran for a while then gave me this error:

""checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!""

I'm trying to install v1.2.3 as 1.2.2 kept crashing.  Its a beta version but was told by the author it's being released soon and appears stable.

> **compiledkernel said:**
> first of all, do you have build-essential package? 

sudo apt-get install build-essential 

then 

tar zxvf nameoffile.tar.gz
cd ~/nameoffile
./configure
make

sudo -i (to become root) 

make install 

I just ran the source isntall for 1.2.2 versioning , and it compiled and installed ok for me.

---

### Post by oldos2er on 2008-01-21
You might need libx11-dev.

---

### Post by brett611 on 2008-01-24
> **oldos2er said:**
> You might need libx11-dev.

installed that, same result

---

### Post by mdpalow on 2008-01-25
it doesn't work when you open a terminal window and type:

```
sudo aptitude install k9copy
```

---

### Post by brett611 on 2008-01-25
> **mdpalow said:**
> it doesn't work when you open a terminal window and type:

```
sudo aptitude install k9copy
```

Technically yes - it installs v1.2.2.  However, it errors out whenever I try to use it.  The developer acknowledged it as a bug based on the error logs and sent me a pre-release of v1.2.3 and asked me to see if it fixed the problem.  But I can't get the tar to install.

So basically, my question is - how do I install a tar.gz file?  all the existing threads that cover this provide instructions that do not 'work' based on the error msg.

---

### Post by Paqman on 2008-01-25
Have a look at the contents of the unzipped folder. It might not be a file called "configure" that you have to run. There may well be a readme in there with some instructions, too.

---

### Post by oldos2er on 2008-01-25
> **brett611 said:**
> installed that, same result

 Have you looked in README or INSTALL for a list of dependencies? 

 Or, go into Synaptic, find k9copy, and look at its dependencies from there.

---

### Post by timjohn7 on 2008-03-20
I have a similar problem with installation of PCManFM 0.3.9.9 tar file.
I've downloaded it, extracted it to ~/Downloads/pcmanfm-0.3.9.9
cd'd to that directory
./configure (all runs well but gives an error at the end regarding gtk2... sorry I don't have the exact message
I've tried make, make install, sudo make, sudo make install... no joy
I do have build-essentials installed
I have given up and am looking at the deb version 0.3.6 of pcmanfm
Why should the installation of tars be so iffy?

---

### Post by stchman on 2008-03-20
> **brett611 said:**
> I'm trying to install a tar.gz of k9copy with no luck.  I've looked at many posts (attached) and psychocats and the install instrux file that came with the tar.gz.  I'm trying to install this version b/c the one in Synaptics doesn't work for me.

Attached is the error details.  Assistance most appreciated.
Thanks!

Why go through the hassle?  You can get the 1.2.3 .deb from [www.getdeb.net](www.getdeb.net)

[http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy)

Download and install.

---

### Post by brett611 on 2008-04-07
> **stchman said:**
> Why go through the hassle?  You can get the 1.2.3 .deb from [www.getdeb.net](www.getdeb.net)

[http://www.getdeb.net/app/K9Copy](http://www.getdeb.net/app/K9Copy)

Download and install.

Probably because your post is the first I've heard of such a site

---

