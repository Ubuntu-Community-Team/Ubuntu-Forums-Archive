---
title: "make command not found"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by andym1966 on 2006-05-05
Hi there,
I'm trying to install apache web server.  I've followed the instructions up until the Compile stage (see below).

Download  	$ lynx [http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)
Extract 	$ gzip -d httpd-NN.tar.gz
$ tar xvf httpd-NN.tar
$ cd httpd-NN
Configure 	$ ./configure --prefix=PREFIX
Compile 	$ make
Install 	$ make install
Customize 	$ vi PREFIX/conf/httpd.conf
Test 	$ PREFIX/bin/apachectl -k start

However, when I run "make" I get the following error,
make: command not found

I read somewhere that Ubuntu does not come with "make" by default.  Does anyone know where and how I can install this? 
  Ubuntu is my first venture into the world of linux, so I'm really a complete novice at this sort of stuff.
Thanks,
Andy.

---

### Post by zerhacke on 2006-05-05
In a terminal,
```
 sudo apt-get install build-essential
```

---

### Post by yabbadabbadont on 2006-05-05
Why don't you install it using apt-get or synaptic?  If you need a newer version, then I understand why, but if not, it would be easier to just install the ubuntu packages.

---

### Post by Sef on 2006-05-05
When using the terminal to get packages it this way.

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

To get to the terminal:  Applications > Accessories > Terminal

By using the update command: you get your computer in sync with the latest repositories.


> Why don't you install it using apt-get or synaptic? If you need a newer version, then I understand why, but if not, it would be easier to just install the ubuntu packages.

Build-essential is not installed by default.  You have to download it.

---

### Post by yabbadabbadont on 2006-05-05
> 
Build-essential is not installed by default.  You have to download it.

Ummm, I was asking the original poster why they didn't use apt-get or synaptic to install apache....  I guess I wasn't clear enough.

---

### Post by Sef on 2006-05-05
> Ummm, I was asking the original poster why they didn't use apt-get or synaptic to install apache.... I guess I wasn't clear enough.

They may not have known about them.  And yes, I misread your post.

---

### Post by patrick295767 on 2006-05-05
apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential

---

### Post by catlett on 2006-05-05
>  Apache HTTP Server 2.2.2 is the best available version

    For details see the Official Announcement and the CHANGES_2.2 list.

    Apache 2.2 add-in modules are not compatible with Apache 2.0 or 1.3 modules. If you are running third party add-in modules, you will need to obtain new modules written for Apache 2.2 from that third party before you attempt to upgrade from Apache 2.0.

        * Unix Source: httpd-2.2.2.tar.gz [PGP] [MD5]
        * Unix Source: httpd-2.2.2.tar.bz2 [PGP] [MD5]
        * Other files
He isn't using synaptic because he might not know what it is. The link he posted leads to an Apache website. This is an excerpt. It does not say use synaptic or use apt-get. It does not list deb files or anything else beside tar files. Also this is his first post so he may not have much experience with ubuntu. He is just folloeing this guide and came up with an error.
What everyone is telling you is that you need the program build-essential to run the commands in your how to.
Go to the terminal and refresh your list of available packages by typing ```
sudo apt-get update
```
Then enter the command to install buil-essential ```
sudo apt-get install build-essential
``` Now run your commands from the how to.
When you get more time go to this link. [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) It explains the different ways to install programs in Ubuntu.

---

### Post by andym1966 on 2006-05-06
Thanks everyone for your advice.  Catlett has got it spot on with his/her analysis of my situation and what I know (or rather don't know).  I've never heard of synaptic or apt-get.  I'll follow your instructions and then go to that website to learn more.
Thanks again!  
Andy.

---

