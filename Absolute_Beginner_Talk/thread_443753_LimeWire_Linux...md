---
title: "LimeWire Linux.."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-14
I downloaded  LimeWireLinux.bin ..

but i have no idea how this works...

I tried like sudo apt-get install LimeWireLinux.bin but it didn't work out..

Yes..I'm new to this..how can I work this out..?

Thank you.. :)

---

### Post by taurus on 2007-05-14
```
cd ~/Desktop
chmod 755 LimeWireLinux.bin
./LimeWireLinux.bin
```
Make sure you have installed java first or limewire won't run.

```
java -version
```

---

### Post by overdrank on 2007-05-14
> **rocketboys said:**
> I downloaded  LimeWireLinux.bin ..

but i have no idea how this works...

I tried like sudo apt-get install LimeWireLinux.bin but it didn't work out..

Yes..I'm new to this..how can I work this out..?

Thank you.. :)

Hi you can try frostwire it works great! :guitar:

---

### Post by rocketboys on 2007-05-14
> **taurus said:**
> ```
cd ~/Desktop
chmod 755 LimeWireLinux.bin
./LimeWireLinux.bin
```
Make sure you have installed java first or limewire won't run.

```
java -version
```

Thank you for your response!

I got this message..

danny@Dan:~$ cd Desktop
danny@Dan:~/Desktop$ chmod 755 LimeWireLinux.bin
danny@Dan:~/Desktop$ ./LimeWireLinux.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.
danny@Dan:~/Desktop$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
danny@Dan:~/Desktop$ sudo apt-get install VM prior
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VM

do I have java? or...and what is VM prior..? :'(

---

### Post by taurus on 2007-05-14
Told you you need to install java first.  ;) 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by lilyoshi13 on 2007-05-14
You should try using BitTorrant instead of limewire.  It is much safer

---

### Post by rocketboys on 2007-05-14
> **taurus said:**
> Told you you need to install java first.  ;) 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Thank you!

I just installed it succesfully!

but now, how can I run? heehe

---

### Post by taurus on 2007-05-14
```
limewire
```
Or there should be an icon in Applications -> Internet.

---

### Post by rocketboys on 2007-05-14
> **taurus said:**
> ```
limewire
```
Or there should be an icon in Applications -> Internet.

Thank you!

I just found it!

:)

---

### Post by jackhewyhx6 on 2007-05-15
I downloaded LimeWireLinux.deb.
But the Gdebi says "Status:[COLOR="Red"]Error:Dependency is not satisfiable: libc6[/COLOR]"!
I had tried sudo apt-get install LimeWireLinux.deb too,but it won't work!

Help Please! Thanks:(

---

### Post by misfitpierce on 2007-05-15
get automatix and it will install frostwire for you and you can put limewire on desktop and...

cd /home/YOURNAME/Desktop
sh LIMWIRENAME.bin

---

### Post by mahy on 2007-05-15
> **jackhewyhx6 said:**
> I downloaded LimeWireLinux.deb.
But the Gdebi says "Status:[COLOR="Red"]Error:Dependency is not satisfiable: libc6[/COLOR]"!
I had tried sudo apt-get install LimeWireLinux.deb too,but it won't work!

Help Please! Thanks:(

you need to install libc6, of course. Fire up Synaptic or try 

sudo apt-get install libc6

HTH

---

### Post by compiledkernel on 2007-05-15
Getdeb's got Frostwire. 

Just use it. 

[http://www.getdeb.net/app.php?name=Frostwire](http://www.getdeb.net/app.php?name=Frostwire)

---

### Post by Benbow on 2007-05-15
Frostwire works like dream. I installed it yesterday without problems and it is ticking over smoothly!
Good luck.

---

