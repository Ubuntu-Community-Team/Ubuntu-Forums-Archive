---
title: "[SOLVED] how i can install adobe reader 7.9 ?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by goodman on 2007-07-29
i downloaded adobe acrobat v7.0.9
in rpm packet 

and i converted it to deb with alien tool

i success in converting and installation 

and acrobat reader icon appear in applications >> office 

but when i click on this icon this message appear 

[IMG]http://img108.imageshack.us/img108/8144/errorny6.jpg[/IMG]

thank u

---

### Post by Nevis on 2007-07-29
Any particular reason why you're using Adobe Acrobat when there's other open source choices? I've always found Acrobat to be a bit of a pain in Windows.

---

### Post by goodman on 2007-07-29
> **Nevis said:**
> Any particular reason why you're using Adobe Acrobat when there's other open source choices? I've always found Acrobat to be a bit of a pain in Windows.

i am beginner ubuntu user and i study how i can install program under this os

i want to learn how i can solve problem such that


thank you

---

### Post by Kosimo on 2007-07-29
Try to run it from terminal:

sudo acrobat

---

### Post by goodman on 2007-07-29
> **Kosimo said:**
> Try to run it from terminal:

sudo acrobat

it doesn't work

sudo: acrobat: command not found

i tray also
sudo acroread

it return 
sudo: acroread: command not found

thank you

---

### Post by goodman on 2007-07-29
may be i can solve this problem if i can log in as root

how i can log in as root ?

---

### Post by pashashome on 2007-07-29
Check this out [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
and this: [http://manishtech.wordpress.com/2007/07/21/enabling-root-login-in-ubuntu/](http://manishtech.wordpress.com/2007/07/21/enabling-root-login-in-ubuntu/).

Good luck, hope that helps.

---

### Post by goodman on 2007-07-29
> **pashashome said:**
> Check this out [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
and this: [http://manishtech.wordpress.com/2007/07/21/enabling-root-login-in-ubuntu/](http://manishtech.wordpress.com/2007/07/21/enabling-root-login-in-ubuntu/).

Good luck, hope that helps.

thank you 

now i learn how i can enable root login


but when i enter as root this message appear again when i tray run acrobat


so how i can remove this program from my system


thank you

---

### Post by pashashome on 2007-07-29
This should do it.
```
dpkg -r Whatever_package_name.deb
```

This should also remove any configuration files.

---

### Post by Nevis on 2007-07-29
You might find useful info in this thread;
[http://ubuntuforums.org/showthread.php?p=3086284](http://ubuntuforums.org/showthread.php?p=3086284)

---

### Post by Copter on 2007-07-30
Guys! What are you doing? What has got to do enabling of root account, which is highly insecure with installing Acrobat Reader? It is normal that sudo acroread takes you nowhere. Please be serious in the Absolute Beginner Talk section.

For beginers it is best to install new software using Synaptic. If you want to use command line then
```

sudo apt-get install package_name

```
installs package_name on your system when you have package_name in your repositories. Or
```

sudo dpkg -i some_file_name.deb

```
when you have some_file_name.deb file in your current directory. As I can see there is some problem with Acrobat Reader in Fiesty. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=acrobat&searchon=all&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=acrobat&searchon=all&subword=1&version=all&release=all") states that there isnt Acrobat Reader version for Fiesty but I can be wrong here. I tried to install it from Adobe web page using 'alien' tool to convert .rpm to .deb
```

sudo apt-get install alien
sudo alien AdobeReader_enu-7.0.9-1.i386.rpm 
sudo dpkg -i adobereader-enu_7.0.9-2_i386.deb 

```
but I got the same message about problems with child process so I cant help you here for now.

As for dpkg -r, according to man pages this **does not** remove any configuration files. dpkg -P does that actually. Type man dpkg and see for yourself. And for loging as root
```

sudo su

```
After that execute apt-get, alien, dpkg and others without using sudo. But remeber, the safest way to install new software is to do it by apt-get or synaptic using official or trusted repositories.

copter :]

---

### Post by goodman on 2007-08-02
> **Nevis said:**
> You might find useful info in this thread;
[http://ubuntuforums.org/showthread.php?p=3086284](http://ubuntuforums.org/showthread.php?p=3086284)



thank you

---

### Post by goodman on 2007-08-02
> **Copter said:**
> Guys! What are you doing? What has got to do enabling of root account, which is highly insecure with installing Acrobat Reader? It is normal that sudo acroread takes you nowhere. Please be serious in the Absolute Beginner Talk section.

For beginers it is best to install new software using Synaptic. If you want to use command line then
```

sudo apt-get install package_name

```
installs package_name on your system when you have package_name in your repositories. Or
```

sudo dpkg -i some_file_name.deb

```
when you have some_file_name.deb file in your current directory. As I can see there is some problem with Acrobat Reader in Fiesty. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=acrobat&searchon=all&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=acrobat&searchon=all&subword=1&version=all&release=all") states that there isnt Acrobat Reader version for Fiesty but I can be wrong here. I tried to install it from Adobe web page using 'alien' tool to convert .rpm to .deb
```

sudo apt-get install alien
sudo alien AdobeReader_enu-7.0.9-1.i386.rpm 
sudo dpkg -i adobereader-enu_7.0.9-2_i386.deb 

```
but I got the same message about problems with child process so I cant help you here for now.

As for dpkg -r, according to man pages this **does not** remove any configuration files. dpkg -P does that actually. Type man dpkg and see for yourself. And for loging as root
```

sudo su

```
After that execute apt-get, alien, dpkg and others without using sudo. But remeber, the safest way to install new software is to do it by apt-get or synaptic using official or trusted repositories.

copter :]



thank you 

about these useful commandns

---

