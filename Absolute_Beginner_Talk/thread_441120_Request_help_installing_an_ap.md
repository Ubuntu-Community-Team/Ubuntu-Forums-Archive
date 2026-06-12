---
title: "Request help installing an ap"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by jimeez on 2007-05-12
I am tearing my hair out trying to get [PWSafe](https://sourceforge.net/project/showfiles.php?group_id=41019&package_id=164907&release_id=478850) installed.  I have successfully extracted the tar.gz to a folder on my root directory
```
/home/jmk/Downloads
```but I'll be damned if I can get the thing to ./make  ./compile, etc..

Any thoughts?

---

### Post by trak87 on 2007-05-12
Is there an associated INSTALL file? This is a text file that will give instructions. Is there first a ./configure option before you run make?

After looking for the INSTALL file, look for a README.

---

### Post by Bachstelze on 2007-05-12
It's in the Ubuntu repositories.

```
sudo apt-get install pwsafe
```

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by taurus on 2007-05-12
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf PasswordSafeSWT-0.6-linux.tar.gz
cd PasswordSafeSWT-0.6-linux
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo checkinstall
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by jimeez on 2007-05-12
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf PasswordSafeSWT-0.6-linux.tar.gz
cd PasswordSafeSWT-0.6-linux
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo checkinstall
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)Getting stuck at ./configure

---

### Post by jimeez on 2007-05-12
```
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ ./configure
bash: ./configure: No such file or directory
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$
```

and no, there is no INSTALL or README file
```
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ dir
bcprov-jdk14-133.jar             libswt-mozilla-gtk-3232.so
blowfishj-2.14.jar               libswt-pi-gtk-3232.so
commons-logging.jar              opencsv-1.1.jar
libcairo-swt.so                  org.eclipse.core.runtime_3.1.0.jar
libswt-atk-gtk-3232.so           org.eclipse.jface_3.1.0.jar
libswt-awt-gtk-3232.so           org.eclipse.osgi_3.1.0.jar
libswt-cairo-gtk-3232.so         passwordsafe-lib.jar
libswt-glx-gtk-3232.so           PasswordSafeSWT.jar
libswt-gnome-gtk-3232.so         pwsafe.sh
libswt-gtk-3232.so               swt.jar
libswt-mozilla-gcc3-gtk-3232.so
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ 

```

And the PWSafe ap that is available in the Ubuntu repositories is a simple command line ap.  Not the one I want.

---

### Post by taurus on 2007-05-12
There is nothing to configure or build in this case.  Try

```
./pwsafe.sh
-or-
sudo ./pwsafe.sh
```

---

### Post by jimeez on 2007-05-12
```
jmk@linux:~$ cd Downloads
jmk@linux:~/Downloads$ cd PasswordSafeSWT-0.6
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ ./pwsafe.sh
bash: ./pwsafe.sh: Permission denied
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ sudo ./pwsafe.sh
sudo: ./pwsafe.sh: command not found
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ sudo ./pwsafe.sh
sudo: ./pwsafe.sh: command not found
jmk@linux:~/Downloads/PasswordSafeSWT-0.6$ 

```

I did find this by double clicking the "pwsafe.sh" file:
```
# == Syntax for calling me =====================================================================

#    [{./|../|/path/}pwsafe.{cmd|sh} [{-|/}{d|D}] [{-|/}{j|J} java options]

#    pwsafe.cmd is needed for WinXYZ and pwsafe.sh should work for Linux and MAC

# == ===========================================================================================

```Thank you again for the replies.

---

### Post by jimeez on 2007-05-13
Found a TODO.lst on the download, and they readily admit that the installation script is FUBAR for Linux.

---

