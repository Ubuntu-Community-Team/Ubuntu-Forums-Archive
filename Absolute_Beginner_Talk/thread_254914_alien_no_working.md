---
title: "alien no working"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-10
sudo alien -i /home/matt/desktop/limewirelinux.rpm

and it won't install it says file not found but it is on my desktop

---

### Post by baldy1324 on 2006-09-10
/home/whatever/Desktop not desktop (case sensative)

---

### Post by catlett on 2006-09-10
You are ebtering the path wrong. desktop is Desktop. Change the path from 
> /home/matt/[COLOR="Red"]d[/COLOR]esktop/limewirelinux.rpm
To this one
```
/home/matt/[COLOR="Red"]D[/COLOR]esktop/limewirelinux.rpm
```
When you are entering a path, use the 'tab' key on your console to finish the path. 
Or the trick I use is I drag and drop the file into the terminal. When dropped, the path to the file will be written ou. So I would do it like this
Open the terminal. Enter 
```
 	sudo alien -i 
```
Then drag and drop the limewire rpm into the terminal. It will print out the path ```
sudo alien -i /home/matt/Desktop/limewirelinux.rpm
```
Press enter.

---

### Post by joshier on 2006-09-10
To this one
"/home/matt/Desktop/limewirelinux.rpm"

Capital D for Desktop.

---

### Post by Devile on 2006-09-10
ok perfect that worked but now it won't run...  i open limewire, and nothing happens...

---

### Post by arkangel on 2006-09-10
what error exaclty do you have ?

---

### Post by Aranel on 2006-09-10
Try entering the command to start it in a terminal. What error do you get?

If it says something about Java not being found in your $PATH, I also encountered that problem when attempting to run Mercury Messenger. After Googling around with little success, I finally tried creating symbolic links in /usr/bin to all of the files in /usr/java/jre1.5.0_06/bin:

```
cd /usr/bin
sudo ln -s /usr/java/jre1.5.0_06/bin/*
```

The latter directory may be slightly different from you, but... you get the picture. Once you've done that, it should work (assuming that that's the error you're getting and that you have Java installed :p ). Good luck.

---

### Post by Devile on 2006-09-10
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

That's the error i'm getting

---

### Post by catlett on 2006-09-10
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```That will install java if you have the correct repositories. If you canot install with that command then change your repos. Like this.
Enter this
```
sudo gedit /etc/apt/sources.list
```Delete everything and enter this into the blank document
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```Make sure to save the document and close it.
Now enter this
```
sudo apt-get update
```Then re-enter the java command 
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

---

### Post by Devile on 2006-09-11
it didn't work... well that worked but limeiwre still wont' open:

Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by Devile on 2006-09-11
i figured it out... i just went into synapic or whatever it is the package thing...  and installed the jre package... that the above requested and now it's fine

---

