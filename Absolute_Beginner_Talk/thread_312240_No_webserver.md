---
title: "No webserver?"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by old_newbie on 2006-12-04
I have installed Ubuntu 6.10 on my pc as the only os. Please bear in mind: I have used Windows only since 1993 and are totally new to Linux. 
My question: How to enable this installation as a webserver? Just for test purposes, not connected to the internet. I wonder how to enable the localhost, where to find php, where to find the web root level, where to find mysql - do i have to find another installation?:-k :-k

---

### Post by hyper_ch on 2006-12-04
Hiya

The install of a webserver is easy. Open the command line terminal and just enter:

sudo apt-get install apache2

This will install the apache2 server on your local machine and it will also already be started. (If you want to re/start or stop the server just enter in the console:  sudo /etc/init.d/apache2 star|restart|stop.)

The server root folder is /var/www/ if I am not mistaken. This means just create an index.html in there, open your webbrowser, enter "localhost" and you should see that index.html

To install mysql it's basically the same:
sudo apt-get install mysqld
and
sudo /etc/init.d/mysqld start|stop|restart
The mysql dbs are normally stored in /var/lib/mysql/

If you want also want to install PHP and everything working together please have a look at this here:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

From page4 it will tell you about mysql, after that apache and php...

---

### Post by old_newbie on 2006-12-04
But..I can't switch to root in the terminal, using my defined user password. It says worng password, sorry. Is it not possible to change to root?:confused:

---

### Post by hyper_ch on 2006-12-04
You are on Ubuntu, you don't need root... you just add "sudo" in front of each command. This will execute the command as root :)

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2
sudo apt-get install mysql
sudo apt-get install wine
sudo .........

:)

---

### Post by old_newbie on 2006-12-04
Ooopss... Well, I tried your command for installing apache, got two nice feedbacks, but finally the answere:  
E: could not find package apache2  
:confused: :-k

---

### Post by hyper_ch on 2006-12-04
Now this is strange.

Please post the output of:

apt-cache search apache2

and the output of:

cat /etc/apt/sources.list

---

### Post by lamego on 2006-12-04
You really need to understand how to install software on Ubuntu, read at:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html)

---

### Post by old_newbie on 2006-12-04
**Here are all my output:**

johno@johno-Linux:~$ apt-cache search apache2
johno@johno-Linux:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

And that's it. Do you have any idea? :confused:

---

### Post by old_newbie on 2006-12-04
My ubuntu-box is not connected tot he internet, am I supposed to be connected in order to install these packages, or are they available on the CD-ROM  - Ubbuntu 6.10? :confused:

---

### Post by hyper_ch on 2006-12-04
Oh, you are supposed to be connected or have the ubuntu dvd.... on the cd is only a small number of frequently used programs... if you would have downloaded the server install cd then apache and webstuff would be on it :)

---

