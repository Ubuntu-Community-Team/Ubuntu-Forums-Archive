---
title: "installing java"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by nick5449 on 2006-04-22
When installing java, i run the command:

 sudo apt-get install fakeroot java-package java-common

It then says:

After unpacking 16.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media Change: Please insert the disc labelled
 ‘Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060217.2)’
in the drive ‘/cdrom/’ and press enter

When I press enter with the CD in the drive its not recognized and just keeps asking for the cd.  Why is it not being recognized?  Thanks.

---

### Post by Qrk on 2006-04-22
I would recommend doing a: 
```
gksudo gedit /etc/apt/sources.list
```

Add a # before the line that refers to the cdrom.

---

### Post by jorn on 2006-04-22
Why gksudo and not just sudo?

---

### Post by nick5449 on 2006-04-22
Okay, I put the # in front of the cdrom directory, which worked...but now Im having another problem.  After I run the command:

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

I get a warning saying:

sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

which appears five times, but doesnt seem to affect anything.   So it continues to install and when it looks like its almost done I get the following error and it aborts:

dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXXwb7sf2/sun-j2re1.5_1.5.0+update06_i386.deb'.
    copy sun-j2re1.5_1.5.0+update06_i386.deb into directory /usr/java/
cp: cannot create regular file `/usr/java/sun-j2re1.5_1.5.0+update06_i386.deb': Permission denied

Aborted (/usr/java/).

So then I tried installing it as a root user and it complained saying I should only run it as a non-root user.  Any suggestions?  Thanks for the help.

---

### Post by Qrk on 2006-04-22
You probably haven't installed the compilers you need. Just do a 

```
sudo apt-get install build-essential
```

to get all your needed tools.


> Why gksudo and not just sudo?

I don't think it makes a difference, just that gksudo looks nicer. However, I've heard that using sudo with a gui app can cause problems.

---

### Post by nick5449 on 2006-04-22
Doing a
```
sudo apt-get install build-essential
```
got rid of the warnings, but it's still aborting because of the same error:
```
dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXXAAJD3k/sun-j2re1.5_1.5.0+update06_i386.deb'.
    copy sun-j2re1.5_1.5.0+update06_i386.deb into directory /usr/java/
cp: cannot create regular file `/usr/java/sun-j2re1.5_1.5.0+update06_i386.deb': Permission denied

Aborted (/usr/java/).
```

---

### Post by Qrk on 2006-04-22
Move the java bin file to your desktop, and then run the command from your desktop. 

```
cd ~/Desktop
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```

This will cause the deb to be made in a folder you have permission to write to. Once the command runs, the deb should be on your desktop. 

Hopefully this works

---

