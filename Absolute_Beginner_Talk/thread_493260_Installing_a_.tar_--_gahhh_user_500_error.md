---
title: "Installing a .tar -- gahhh user 500 error"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-07-05
I am having one heck of a time installing this darn software.  I know that it works becuase i had someone help me before with the install, but had to wipe my test pc because i fiddled with the video card settings; long story short, i need help installing this darn .tar file.

So ---
Package name: AventailConnect-Linux.tar

I goto the command line

su -- enter root password
root@linux-laptop:># tar xvf AventailConnect-Linux.tar
(this unzips 3 files into my /home/linux folder)
***
AventailConnect-Linux-8.70.447.tar.bz2
version
install.sh
***

I than: tar xvjf AventailConnect-Linux-8.70.447.tar.bz2
(this unzips the files to a new folder, not the one i want on the root of my homedir or any better place, but:

***
root@linux-laptop:/home/linux# tar xvjf AventailConnect-Linux-8.70.447.tar.bz2
usr/
usr/local/
usr/local/Aventail/
usr/local/Aventail/help/
usr/local/Aventail/help/connect_tunnel_help.html
usr/local/Aventail/man/
usr/local/Aventail/man/ct.5
usr/local/Aventail/certs.tar.bz2
usr/local/Aventail/stopct
usr/local/Aventail/avpconf
usr/local/Aventail/aventail-icon-32x32.gif
usr/local/Aventail/ctpid.sh
usr/local/Aventail/cttel.pl
usr/local/Aventail/startct.sh
usr/local/Aventail/startctui.sh
usr/local/Aventail/xg-ui/
usr/local/Aventail/xg-ui/aventail-icon.gif
usr/local/Aventail/xg-ui/xgswing.jar
usr/local/Aventail/uninstall.sh
usr/local/Aventail/runcmd.sh
usr/local/Aventail/AvConnect
***

I am sure i am missing a command to simply extract all of the files 1 time, instead of this multiple time business, but i am still green with all things linux, im trying.

So --- the crux of my problem, i cannot seem to get this darn thing to install.  I browse to /home/linux/usr/local/Aventail and try ./install, ./make --- nada, i know the files arent there.  HELP

so here is what i think is wrong --- permissions are set to 500 and also, on the first tar -xvf -- it unzipped an install.sh and version file, should they all be in the same spot?

Here are the permissions from dir -l in both places:

This is /home/linux:
-rw-r--r-- 1 linux linux  309257 2007-07-03 12:05 ABSTRACT-BlueRidge_1280x1024.png
-rw-rw-r-- 1   500   500 1012871 2006-08-03 15:20 AventailConnect-Linux-8.70.447.tar.bz2
-rw-rw-rw- 1 linux linux 1034240 2007-07-05 12:04 AventailConnect-Linux.tar
drwxr-xr-x 2 linux linux    4096 2007-07-03 22:21 Desktop
lrwxrwxrwx 1 linux linux      26 2007-07-03 11:46 Examples -> /usr/share/example-content
-rwxrwxr-x 1   500   500   11937 2006-08-03 15:20 install.sh
drwxrwxr-x 3   500   500    4096 2006-08-03 15:20 usr
-rw-rw-r-- 1   500   500       9 2006-08-03 15:20 version


This is /home/linux/usr/local/Aventail:
-rwxrwxr-x 1 500 500 755652 2006-08-03 15:20 AvConnect
-r--r--r-- 1 500 500   1365 2006-08-03 15:20 aventail-icon-32x32.gif
-rwxrwxr-x 1 500 500  15304 2006-08-03 15:20 avpconf
-r--r--r-- 1 500 500  70933 2006-08-03 15:20 certs.tar.bz2
-rw-rw-r-- 1 500 500    169 2006-08-03 15:20 ctpid.sh
-rw-rw-r-- 1 500 500  17355 2006-08-03 15:20 cttel.pl
drwxrwxr-x 2 500 500   4096 2006-08-03 15:20 help
drwxrwxr-x 2 500 500   4096 2006-08-03 15:20 man
-rw-rw-r-- 1 500 500    690 2006-08-03 15:20 runcmd.sh
-rw-rw-r-- 1 500 500    383 2006-08-03 15:20 startct.sh
-rw-rw-r-- 1 500 500   2135 2006-08-03 15:20 startctui.sh
-rwxrwxr-x 1 500 500   4252 2006-08-03 15:20 stopct
-rw-rw-r-- 1 500 500   1217 2006-08-03 15:20 uninstall.sh
drwxrwxr-x 2 500 500   4096 2006-08-03 15:20 xg-ui


Any help would be greatly appreciated, I have been working on this goofy problem for about 4 hours and its driving me batty!

Thank you

---

### Post by taurus on 2007-07-05
Try

```
cp AventailConnect-Linux-8.70.447.tar.bz2  /
cd /
tar xvjf AventailConnect-Linux-8.70.447.tar.bz2
```
Now, your Aventail is unpacked in /usr/local/Aventail/.

---

### Post by annda on 2007-07-05
have you tried running the install script after extracting the initial archive? go to the directory where the file is located and:

```
./install.sh
```

---

### Post by Raineer on 2007-07-05
What happens if you:

```
chmod +x install.sh
./install.sh
```

I have a feeling the install script might un-tar that second tar.bz2 for you.

---

### Post by williamburn on 2007-07-05
copied the files -- still nada :

root@linux-laptop:/usr/local/Aventail# dir -l
total 916
-rwxrwxr-x 1  500  500 755652 2006-08-03 15:20 AvConnect
-r--r--r-- 1  500  500   1365 2006-08-03 15:20 aventail-icon-32x32.gif
-rwxrwxr-x 1  500  500  15304 2006-08-03 15:20 avpconf
-r--r--r-- 1  500  500  70933 2006-08-03 15:20 certs.tar.bz2
-rw-rw-r-- 1  500  500    169 2006-08-03 15:20 ctpid.sh
-rw-rw-r-- 1  500  500  17355 2006-08-03 15:20 cttel.pl
drwxrwxr-x 2  500  500   4096 2006-08-03 15:20 help
-rwxr-xr-x 1 root root  11937 2007-07-05 15:47 install.sh
drwxrwxr-x 2  500  500   4096 2006-08-03 15:20 man
-rw-rw-r-- 1  500  500    690 2006-08-03 15:20 runcmd.sh
-rw-rw-r-- 1  500  500    383 2006-08-03 15:20 startct.sh
-rw-rw-r-- 1  500  500   2135 2006-08-03 15:20 startctui.sh
-rwxrwxr-x 1  500  500   4252 2006-08-03 15:20 stopct
-rw-rw-r-- 1  500  500   1217 2006-08-03 15:20 uninstall.sh
-rw-r--r-- 1 root root      9 2007-07-05 15:47 version
drwxrwxr-x 2  500  500   4096 2006-08-03 15:20 xg-ui

./install -- this produces
root@linux-laptop:/usr/local/Aventail# ./install.sh
./install.sh: 22: function: not found

./startctui.sh  -- this produces
root@linux-laptop:/usr/local/Aventail# ./startctui.sh
bash: ./startctui.sh: Permission denied

Do you think it might be a permission problem?  I havent really installed anything, i have simply unpacked the files -- therefore, i still need to install the package, i think...

---

### Post by annda on 2007-07-05
i don't think you are supposed to untar the second archive manually (AventailConnect-Linux-8.70.447.tar.bz2). the install script should do it for you, just as Raineer said.

sometimes running via

```
sh install.sh
```

helps.

---

### Post by williamburn on 2007-07-05
./install.sh: 24: Syntax error: "}" unexpected
root@linux-laptop:/usr/local/Aventail# sh install.sh
install.sh: 22: function: not found

install.sh: 24: Syntax error: "}" unexpected
root@linux-laptop:/usr/local/Aventail#

---

### Post by annda on 2007-07-05
oops, bad script? you could post the contents of install.sh (it's a text file) so someone could tell you what is wrong with it (lines 22 and 24). i don't know enough to help you. maybe the nice folks in the programming forum?

have you googled to see if other people have trouble with it under ubuntu too?

---

### Post by mgaz on 2008-01-05
Just issue "sudo /bin/bash ./install.sh" instead of ./install.sh. This works without problems

---

### Post by Almumin on 2008-04-01
mgaz,

I did the "/bin/bash ./startctui.sh command. i don't see anything. Is there something else that needs to be running? Java is installed the /usr/local/Aventail folder is installed. What am I missing?:(

---

