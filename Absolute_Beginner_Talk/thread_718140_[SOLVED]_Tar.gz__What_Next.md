---
title: "[SOLVED] Tar.gz  What Next?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Mad_Dawg on 2008-03-07
I have, on my desktop, the file hplip-2.7.12.tar.gz.  My understanding is that it is like a zip file.  How do I unpack it?

---

### Post by A4006 on 2008-03-07
Double-click it.

---

### Post by Sef on 2008-03-07
Read [How to Install Anything on Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Mad_Dawg on 2008-03-07
Ok, now I have this thing that looks like a file directory.  How do I get it installed?

---

### Post by bodhi.zazen on 2008-03-07
In general you should install from the repos if at all possible. 

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

=================

To compile :

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```

	download the source code, unpackage.

	Open a terminal, cd into the package directory.

	Now, 

	[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
	[*]List the options: ```
./configure --help | less
```You may scroll through the output with up and down arrows, page up, page down ... 
	Type q to exit less.


	[*]./configure --prefix=/usr
	[*]make
	[*]sudo checkinstall -D[/list]

	[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

	[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Mad_Dawg on 2008-03-07
Thank you to all who have helped.  I am just not getting this.  I have the HPLIP tar thing extracted to a file on the desktop, but I don't know what to do with it.  I just can't get the thing installed.

---

### Post by Snakob808 on 2008-03-07
In a terminal, go into the tar directory.  

if there is a configure file, you'll want to type-

```
./configure
```

Type...

```
sudo make
```

and then...

```
sudo make install
```

---

### Post by Mad_Dawg on 2008-03-07
thank you,  this is what i get:

> 

no rule to make target i'nstall'. stop.



---

### Post by bodhi.zazen on 2008-03-07
hplip is in the repos :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hplip&searchon=name&subword=1&version=all&release=all)

Enable your repos 

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)


and ```
sudo apt-get install hplip
```

---

