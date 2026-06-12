---
title: "Help installing wine."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by burritoking924 on 2007-03-06
I would just like to say that i have never ran anything other then Windows.

I am using the 64 bit version of Edgy along with my Athlon 3700+ processor. I downloaded wine from the website and read on the wiki a way to force install wine on 64 bit computers. It said to run this in terminal

cd ~/Desktop 
sudo dpkg --force-architecture -i wine_*_i386.deb

After that I get a message saying that there was a problem with the install.
The file is named 

wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb

IDK whats wrong so if anybody can help me it will be greatly appreciated.

---

### Post by invalid on 2007-03-06
Please post the exact error you receive.

---

### Post by burritoking924 on 2007-03-06
chris@chris-desktop:~$ cd ~/Desktop 
chris@chris-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_*_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 87581 files and directories currently installed.)
Preparing to replace wine 0.9.32~winehq0~ubuntu~6.10-1 (using wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
chris@chris-desktop:~/Desktop$

---

### Post by invalid on 2007-03-06
Try```
sudo apt-get install libartsc0
```

---

### Post by burritoking924 on 2007-03-06
Nope. Error is

chris@chris-desktop:~$ sudo apt-get install libartsc0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libartsc0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libartsc0 has no installation candidate
chris@chris-desktop:~$ cd ~/Desktop 
chris@chris-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_*_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 87581 files and directories currently installed.)
Preparing to replace wine 0.9.32~winehq0~ubuntu~6.10-1 (using wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
chris@chris-desktop:~/Desktop$

---

### Post by invalid on 2007-03-06
I would use synaptic to find the package which contains libartsc0. Once you have installed this, you will be able to continue with your wine installation.

---

### Post by burritoking924 on 2007-03-07
I had to download it off a website then install it. It installed with no problems. One last question that is going to sound really stupid but how do I use it.  I tried to run a .exe file and it would give me the same message as it always would. Just to say the file was the itunes7.1 installer

---

### Post by Sicarul on 2007-03-07
Right click the exe, select open with and write Wine on a text box on the window that you can choose a lot of applications.

---

### Post by invalid on 2007-03-07
> **burritoking924 said:**
> I had to download it off a website then install it. It installed with no problems. One last question that is going to sound really stupid but how do I use it.  I tried to run a .exe file and it would give me the same message as it always would. Just to say the file was the itunes7.1 installer

From a terminal you can use```
wine application.exe
```

---

### Post by burritoking924 on 2007-03-09
Thanks for all your help. Got it up and running.

---

