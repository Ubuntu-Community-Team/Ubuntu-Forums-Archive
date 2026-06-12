---
title: "Problem installing Adobe Reader"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-17
I downloded the Adobe Reader 7.0.9 to my Desktop, then clicked on 'Extract here'.

Then I clicked on the install file, which gave me options of, 'run', 'run in terminal' and 'display'.

When I tried 'run' nothing happened.  When I tried 'run in terminal', I got this.

>>>
This installation requires 111 MB of free disk space.
 
Enter installation directory for Adobe Reader 7.0.9 [/usr/local/Adobe/Acrobat7.0] 
 
Directory "/usr/local/Adobe/Acrobat7.0" does not exist.
Do you want to create it now? [y]  
mkdir: cannot create directory `/usr/local/Adobe': Permission denied
 
ERROR: Cannot make directory "/usr/local/Adobe/Acrobat7.0".
 
Enter installation directory for Adobe Reader 7.0.9 [/usr/local/Adobe/Acrobat7.0] 
>>>

I would appreciate it if someone would tell me how better to get this installed.  Thanks.

---

### Post by taurus on 2007-05-17
Try to install it from a terminal with the sudo in front to install it to /usr/local/Adobe/Acrobat7.0.

```
cd ~/Desktop
chmod 755 **filename**
sudo ./**filename**
```

---

### Post by gitfiddler on 2007-05-17
Another method is explained here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> Try to install it from a terminal with the sudo in front to install it to /usr/local/Adobe/Acrobat7.0.

```
cd ~/Desktop
chmod 755 **filename**
sudo ./**filename**
```

Thanks for your help.  I tried this but must be making an error somewhere.

>>>
qwer@qwer-desktop:~$ cd ~/Desktop
qwer@qwer-desktop:~/Desktop$ chmod 755 AdobeReader_enu-7.0.9-1.i386.tar.gz
qwer@qwer-desktop:~/Desktop$ sudo AdobeReader_enu-7.0.9-1.i386.tar.gz
Password:
sudo: AdobeReader_enu-7.0.9-1.i386.tar.gz: command not found

qwer@qwer-desktop:~/Desktop$ sudo ./AdobeReader_enu-7.0.9-1.i386.tar.gz
./AdobeReader_enu-7.0.9-1.i386.tar.gz: 1: Syntax error: ")" unexpected

qwer@qwer-desktop:~/Desktop$ chmod 755 AdobeReader_enu-7.0.9-1.i386.tar.gz
qwer@qwer-desktop:~/Desktop$ sudo ./AdobeReader_enu-7.0.9-1.i386.tar.gz
./AdobeReader_enu-7.0.9-1.i386.tar.gz: 1: Syntax error: ")" unexpected
qwer@qwer-desktop:~/Desktop$ 
<<<

---

### Post by taurus on 2007-05-17
I thought that thing is in .bin?  What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> I thought that thing is in .bin?  What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

Thanks again.

qwer@qwer-desktop:~$ ls -la ~/Desktop
total 43200
drwxr-xr-x  3 qwer qwer     4096 2007-05-16 20:59 .
drwxr-xr-x 33 qwer qwer     4096 2007-05-17 07:45 ..
drwxr-xr-x  2 qwer qwer     4096 2007-01-05 13:57 AdobeReader
-rwxr-xr-x  1 qwer qwer 44165526 2007-05-16 20:49 AdobeReader_enu-7.0.9-1.i386.tar.gz
-rw-r--r--  1 qwer qwer     6954 2007-04-10 09:10 freecell.desktop
qwer@qwer-desktop:~$

---

### Post by taurus on 2007-05-17
```
cd ~/Desktop/AdobeReader
ls -la
```

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> ```
cd ~/Desktop/AdobeReader
ls -la
```


>>>

qwer@qwer-desktop:~$ cd ~/Desktop/AdobeReader
qwer@qwer-desktop:~/Desktop/AdobeReader$ ls -la
total 112920
drwxr-xr-x 2 qwer qwer      4096 2007-01-05 13:57 .
drwxr-xr-x 3 qwer qwer      4096 2007-05-16 20:59 ..
-rw-r--r-- 1 qwer qwer   6901760 2007-01-05 13:57 COMMON.TAR
-rw-r--r-- 1 qwer qwer 108441600 2007-01-05 13:57 ILINXR.TAR
-rwxr-xr-x 1 qwer qwer     34770 2007-01-05 13:56 INSTALL
-rw-r--r-- 1 qwer qwer     28978 2005-02-23 07:39 LICREAD.TXT
-rw-r--r-- 1 qwer qwer     79601 2006-05-05 14:54 ReadMe.htm
qwer@qwer-desktop:~/Desktop/AdobeReader$ 

<<<

---

### Post by taurus on 2007-05-17
> **L Campbell said:**
> >>>

qwer@qwer-desktop:~$ cd ~/Desktop/AdobeReader
qwer@qwer-desktop:~/Desktop/AdobeReader$ ls -la
total 112920
drwxr-xr-x 2 qwer qwer      4096 2007-01-05 13:57 .
drwxr-xr-x 3 qwer qwer      4096 2007-05-16 20:59 ..
-rw-r--r-- 1 qwer qwer   6901760 2007-01-05 13:57 COMMON.TAR
-rw-r--r-- 1 qwer qwer 108441600 2007-01-05 13:57 ILINXR.TAR
-rwxr-xr-x 1 qwer qwer     34770 2007-01-05 13:56 [COLOR="Red"]INSTALL[/COLOR]
-rw-r--r-- 1 qwer qwer     28978 2005-02-23 07:39 LICREAD.TXT
-rw-r--r-- 1 qwer qwer     79601 2006-05-05 14:54 ReadMe.htm
qwer@qwer-desktop:~/Desktop/AdobeReader$ 

<<<

There you go.

```
sudo ./INSTALL
```

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> There you go.

```
sudo ./INSTALL
```


Oops! It didn't seem to like that.   :-(

>>>
qwer@qwer-desktop:~$ sudo ./INSTALL
Password:
sudo: ./INSTALL: command not found

qwer@qwer-desktop:~$ sudo ./install
sudo: ./install: command not found
qwer@qwer-desktop:~$ 

<<<

---

### Post by taurus on 2007-05-17
Oops.  You are in the wrong directory.

```
cd **~/Desktop/AdobeReader**
sudo ./INSTALL
```

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> Oops.  You are in the wrong directory.

```
cd **~/Desktop/AdobeReader**
sudo ./INSTALL
```


I believe we have a winner.   :-)

Many thanks for your help and patience.

>>>
qwer@qwer-desktop:~$ sudo ./INSTALL
Password:
sudo: ./INSTALL: command not found
qwer@qwer-desktop:~$ sudo ./install
sudo: ./install: command not found
qwer@qwer-desktop:~$ cd ~/Desktop/AdobeReader
qwer@qwer-desktop:~/Desktop/AdobeReader$ sudo ./INSTALL
Password:
 
This installation requires 111 MB of free disk space.
 
Enter installation directory for Adobe Reader 7.0.9 [/usr/local/Adobe/Acrobat7.0] 
 
Directory "/usr/local/Adobe/Acrobat7.0" does not exist.
Do you want to create it now? [y]  
/usr/local/Adobe/Acrobat7.0
 
Installing platform independent files ... Done
 
Installing platform dependent files ... Done

Do you want to install the browser plugin ? [y/n] y

This will install the browser plugin for acroread.

Do you want to perform automatic installation ? [y/n] 
y


Trying to install plugin for browser - firefox
Installing plugin in /usr/lib/firefox/firefox
Installation successful. /usr/lib/firefox/plugins/nppdf.so


Trying to install plugin for browser - mozilla
Installing plugin in /usr/lib/firefox/firefox
The plugin seems to be already installed. Are you sure you want to overwrite ? [y/n] 
y
Installation successful. /usr/lib/firefox/plugins/nppdf.so


Finished with automatic install.
Do you want to perform manual installation ? [y/n] 
n


If you are facing any problem in getting the installation to work for your browser, please copy the following file to the plugin folder of the browser:
/usr/local/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

In case of difficulties please refer to the documentation provided along with the browser for addition of new plugins.
Please login again for changes to MIME types and icons to take effect.
 
qwer@qwer-desktop:~/Desktop/AdobeReader$ 

<<<

---

### Post by taurus on 2007-05-17
Looks good to me.  You should see an icon for the Reader in Applications -> Office and if you look at the plugins for firefox,

```
about:plugins
```
You should see Acrobat Reader on the list.

---

### Post by L Campbell on 2007-05-17
> **taurus said:**
> Looks good to me.  You should see an icon for the Reader in Applications -> Office and if you look at the plugins for firefox,

```
about:plugins
```
You should see Acrobat Reader on the list.

Yup, its ALL there.

I really appreciate your help.

---

