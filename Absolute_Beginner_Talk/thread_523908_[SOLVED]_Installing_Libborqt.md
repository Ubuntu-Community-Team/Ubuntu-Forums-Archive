---
title: "[SOLVED] Installing Libborqt"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2007-08-12
I have been downloading some avi's in parts and  I need to join them together. I would prefer a GUI. I have installed Avidemux and it does not work consistently. Some Avi files it does not recognise, such as 
Name.avi.001. I do not like using cat because it involves a lot of typing if there are 8 parts to the file. I am therefore looking at installing Hjsplit for linux.

Hjsplit requires that I install  Libborqt. I have downloaded it, extracted it to /tmp/libborqt and have tried to run the install.sh but can not do so. I have opened up terminal in tmp/libborqt folder, typed "sudo install.sh"  Bash reports install.sh command not found. What should I have typed? The readme file states:

Just run install.sh as root in order to install these Kylix 3
libraries.

Step by step:
1. > su
2. enter root password
3. # ./install.sh
4. # exit


But su does not work in Ubuntu.

Apart from the install.sh file there are also some .so files in the extracted folder.

---

### Post by schorsch on 2007-08-12
Try

```
sudo ./install.sh
```

in the directory /tmp/libborqt in a terminal session and enter your password when asked for.

---

### Post by Robbyx on 2007-08-12
I tried your code and there was more of a response. This is what happened:

robin@robin-desktop:/tmp/libborqt$ sudo ./install.sh
Password:
[: 12: ==: unexpected operator
robin@robin-desktop:/tmp/libborqt$ sudo ./install.sh
cp: `libborqt-6.9.0-qt2.3.so' and `libborqt-6.9-qt2.3.so' are the same file
[: 12: ==: unexpected operator
robin@robin-desktop:/tmp/libborqt$ 

This is the contents of install.sh

#! /bin/sh

install -d /usr/lib/kylix3/
install -m 755 libborqt-6.9.0-qt2.3.so /usr/lib/kylix3/libborqt-6.9.0-qt2.3.so

cd /usr/lib/kylix3/
cp -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

grep -q "^/usr/lib/kylix3\$" /etc/ld.so.conf
if [ $? == 1 ]; then
  echo /usr/lib/kylix3 >> /etc/ld.so.conf
fi

/sbin/ldconfig

---

### Post by bwtranch on 2007-08-12
To be permanent root in Ubuntu, you have to "sudo su" and enter the password, then you know you are there when it changes to the # like this root@jim-desktop:/home/jim#

---

### Post by schorsch on 2007-08-12
@robbyx: where did you get the packaged libborqt file from? I just installed the one from

[URL="http://sourceforge.net/project/downloading.php?groupname=kylixlibs&filename=kylixlibs3-borqt-3.0-2.tar.gz&use_mirror=puzzle"]
here[/URL]

and it works like a charm with the instructions I mentioned before.

@bwtranch: Please stop posting stupid things as under Ubuntu you DO NOT NEED permanent root access.  It would be just TO DANGEROUS if you enter a command in a root shell that could kill the whole OS.

---

### Post by Robbyx on 2007-08-12
Strange. I downloaded it from your suggested site and I still get the errer message. Can you suggest why?

---

### Post by schorsch on 2007-08-12
.. you unpacked the sources to another directory, changed to it and did an

```
sudo ./install.sh
```
??

---

### Post by Robbyx on 2007-08-12
What I did was to go to file menu,  and chose open in terminal. I then ran your commands from within the opened terminal.

---

### Post by BlackAnthrax on 2007-08-12
Haha!!
BWT, who taught you that? Not to brag or anything...
But yes, this method will work.
:lolflag:

---

### Post by Robbyx on 2007-08-12
It should work but for me it is not and I get the error message referred to above. So I still have not installed the files.

---

### Post by Robbyx on 2007-08-13
I am still getting the error message. I wonder if it is due to the repeat copy because I am running the install program more than once. Here is the error message:

robin@robin-desktop:~/tmp/libborqt$ sudo ./install.sh
Password:
cp: `libborqt-6.9.0-qt2.3.so' and `libborqt-6.9-qt2.3.so' are the same file
[: 12: ==: unexpected operator
robin@robin-desktop:~/tmp/libborqt$ 



Is there a way of telling if the package has installed?

---

### Post by schorsch on 2007-08-13
You can execute the commands in the script manually step by step:

**Step 1**: Is there a directory /usr/lib/kylix3?
```
ls -ld /usr/lib/kylix3
```
If yes, skip to **Step 2**
If not, do
```
sudo mkdir /usr/lib/kylix3
```

**Step 2**: Is there a file /usr/lib/kylix3/libborqt-6.9-qt2.3.so?
```
ls -l /usr/lib/kylix3/libborqt-6.9-qt2.3.so?
```
If  yes, skip to **Step 3**.
if not, do
```
sudo cp /tmp/libborqt/libborqt-6.9-qt2.3.so  /usr/lib/kylix3/libborqt-6.9-qt2.3.so
```

**Step 3**:
Add a line to the file /etc/ld.so.conf:
```
sudo echo /usr/lib/kylix3 >> /etc/ld.so.conf
```

**Step 4**:
```
sudo /sbin/ldconfig
```

That should do the trick.

---

### Post by Robbyx on 2007-08-13
> Step 3:
Add a line to the file /etc/ld.so.conf:
Code:

sudo echo /usr/lib/kylix3 >> /etc/ld.so.conf

Step 4:
Code:

sudo /sbin/ldconfig



Re step 3
There is some text in the file but I do not know if it is the extra text required by step 3. I can not tell from your step 3 what that line should be

Currently it is:

include /etc/ld.so.conf.d/*.conf

Code 4
I ran your code from the installed directory, sudo asked for the password and nothing happened. I assume it has installed properly.

I then went on to install HJsplit and that does not work, but before I ask about it are you satisfied that libborqt is properly installed?

---

### Post by schorsch on 2007-08-13
The code in step 3 just adds the line "/usr/lib/kylix3" to the file /etc/ld.so.conf. This is necessary so that programs know where to look for libraries (like .dll under windows). After just executing step 3 you have to execute step 4 again; this command looks in the file /etc/ld.so.sonf and generates a cache file /etc/ld.so.cache that is used by binaries to locate the needed libraries.

---

### Post by Robbyx on 2007-08-13
Thank you for your help getting  libborqt to work. I think it is properly installed. I have now gone on to HJsplit itself. When I click on the hjsplitx file in /robin/.hjsplit nothing happens. It does not open and there is no error message. Perhaps I can not run executable files by double clicking them. I do not know.

The instructions that came with the file said:

> (2) Copy HJSplitLX to some location on your harddisk
(3) Start HJSplit for Linux with ./HJSplitLX


I have also tried running hjsplit in terminal and this is what I get:

[email]robin@robin-desktop:~/.hjsp[/email]lit$ ./HJSplitLX
./HJSplitLX: symbol lookup error: ./HJSplitLX: undefined symbol: initPAnsiStrings
[email]robin@robin-desktop:~/.hjsp[/email]lit$

---

### Post by schorsch on 2007-08-13
This tool seems to be clever as it is not looking in /usr/lib/kylix3 for the libborqt-library :confused:  

```
$ ldd HJSplitLX 
        not a dynamic executable
``` ... pfffv .....

After typing
```
 ln -s /usr/lib/kylix3/libborqt-6.9-qt2.3.so /usr/lib/libborqt-6.9-qt2.3.so
```
in a terminal window you are able to start the tool either by clicking in a nautilus window or by typing "./HJSplitLX" in a terminal window when standing in the directory with the binary in it.
Of course you could just copy  "/usr/lib/kylix3/libborqt-6.9-qt2.3.so" to "/usr/lib/libborqt-6.9-qt2.3.so", that would do the trick, too. But then you will not be able to uninstall the libborqt-libraries with the provided uninstall skript ....

---

### Post by Robbyx on 2007-08-13
Thank you for that last bit of code. I can now run hj-split. It is a shame HJsplit is not in a repository.

I would liike to add it to the sound and video section of the applications menu. How do I do it?

---

### Post by schorsch on 2007-08-13
System --> Preferences --> Main Menu

then choose the "Sound and Video" section.

On the right there is a button called "+ New Item". Click there and you are able to add a new menu item. "Name" is just a name, with browse you can search for the executable and after clicking on the "No Icon" button you are able to choose the icon you want.

Glad to hear that it works finally; could you please mark the thread as solved when everything works?

---

### Post by wilerk on 2007-12-20
WOEHAHAHA I downloaded the windows version and double clicked the exe and believe it or not but it runs!

---

### Post by IndianaThreepwood on 2008-01-04
While Linux will not natively run an exe file, if you have WINE installed, double clicking an exe will cause WINE to run it.
This is by far the most simple way of using HJSplit in Ubuntu, at least for now - maybe they'll bring out a .deb version that installs easily :)

---

