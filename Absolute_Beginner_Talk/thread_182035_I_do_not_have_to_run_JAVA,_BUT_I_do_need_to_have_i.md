---
title: "I do not have to run JAVA, BUT I do need to have it installed?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by keith whitehouse on 2006-05-25
Hi there,

I am trying to migrate from Windows and have been having all sorts of problems, but very slowly getting there.

In Windows I have a program ProjectX which needs to have installed the Java Runtime program.

I have just downloaded the program from Sun which left it on the desktop. Using Suns recommendation I 

keith@ubuntu:~/Desktop$ ./j2re-1_4_2_11-linux-i586.bin

which brought up the Suns Licence and then it installed a large amount of files. which I can post the Terminal output if required.

When I try to open the program ProjectX by double clicking on the .jar file within the program it just brings up the contents of the .jar file, but it does not start the program. In Windows this action would have started the program. Any help would be appreciated.

best regards keith

---

### Post by an.echte.trilingue on 2006-05-25
see this page near the bottom on how to install Java properly:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Sef on 2006-05-25
Here's how to install Java:

1) Need to [Add the Repsositories.]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

2) Go to [Restricted Formats.]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by keith whitehouse on 2006-05-25
Hi there,

thanks for the quick reply. As the java program has un-archived and placed a lot of files on the computer, do I have to remove them all (HOW) before I can start again using your link.

best regards keith

---

### Post by keith whitehouse on 2006-05-25
Hi an echte trilingue,

I followed your link but I could not find version 6 so I downloaded version 7, I also downloaded fakeroot.

The Terminal output is

keith@ubuntu:~$ cd /home/keith/Desktop
keith@ubuntu:~/Desktop$ chmod +x jre-1_5_0_07-linux-i586.bin
keith@ubuntu:~/Desktop$ fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found
keith@ubuntu:~/Desktop$ sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
Password:
dpkg: error processing sun-j2re1.5_1.5.0+update07_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update07_i386.deb
keith@ubuntu:~/Desktop$ sudo dpkg -i sun-j2re1.5_1.5.0+update07_i586.deb
dpkg: error processing sun-j2re1.5_1.5.0+update07_i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update07_i586.deb
keith@ubuntu:~/Desktop$

what have I managed to do wrong?

best regards keith

---

### Post by mlind on 2006-05-25
well you didn't seem to read instructions provided by RestrictedFormats wiki entry properly.
You need to install *fakeroot, java-package, java-common* packages using apt-get.

---

### Post by keith whitehouse on 2006-05-25
Hi mlind,

the line you refer to is

Install the install fakeroot java-package java-common packages.

You might know that there are 3 files, me in my ignorance because the names are not seperated by a comma thought that it was just a single download, although I should have got the hint because of the final s

best regards keith

---

### Post by mlind on 2006-05-25
[QUOTE=keith whitehouse]Hi mlind,

the line you refer to is

Install the install fakeroot java-package java-common packages.

You might know that there are 3 files, me in my ignorance because the names are not seperated by a comma thought that it was just a single download, although I should have got the hint because of the final s

best regards keith[/QUOTE]

yes, these things are somewhat confusing at best :mrgreen: 
Atleast it's common between applications that command-line
parameters are separated only by whitespace.

---

### Post by keith whitehouse on 2006-05-25
Hi Mlind,

I have downloaded the other 2 files and everything installed ok, but I still cannot open ProjectX yet, the .jar file when clicked just shows the contents of the .jar file but does not start it. I will work on it.

I really appreciate your time and trouble

best regards keith

---

### Post by mlind on 2006-05-25
You can test that your installation was succesfull by

```

java -version
javac -version

```

You should see version information about Sun's Java. If not, you must use
update-alternatives script to get /usr/bin/java to point on correct java.
(maybe for javac too)
```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```


For running jar's, you probably know that they're invoked by
```

java -jar myprogram.jar

```

---

### Post by Sef on 2006-05-25
> well you didn't seem to read instructions provided by RestrictedFormats wiki entry properly.
You need to install fakeroot, java-package, java-common packages using apt-get.

You don't have to use them.  Both java for Breezy and Dapper are in Multiverse.

> Ubuntu 6.06

Thanks to a redistribution license change from Sun, official Sun java packages are now available in the multiverse repositories. Install it from the Applications -> Add/Remove... menu, or install the sun-java5-bin package.
Ubuntu 5.10

For Ubuntu 5.10 (Breezy Badger), the easiest method is to use the Blackdown Java 1.4 installer from Multiverse. To install Java with the installer, just install the j2re1.4 package. 

[RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

Dapper's download gives you 1.5.0.06

---

### Post by keith whitehouse on 2006-05-26
Hi mlind,

basically I did not know any of the above, but I do now and the information will be stored in my file "knowledge".

my version is

keith@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
keith@ubuntu:~$ javac -version

I have tried to install a few too many java programs in my quest to get ProjectX to work, and I would be happy if I could remove them, is there any chance of being able to do this please

My problem lies with a program ProjectX which I now find out comes with its own java so that it needs nothing else to run. In "Windows" when you click the ProjextX.exe file it opens a window and you can see it creating ProjectX. I cannot get it to do this in Ubuntoo

best regards keith

---

### Post by mlind on 2006-05-26
[QUOTE=keith whitehouse]Hi mlind,

basically I did not know any of the above, but I do now and the information will be stored in my file "knowledge".

my version is

keith@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
[/QUOTE]

There's one last thing you need to do. Your Ubuntu environment is still configured
for GNU's java, where you would wan Sun's instead. You should execute
```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```

and choose Sun's java. Then try java -version, and you should see version info
for correct jvm this time.

[QUOTE=keith whitehouse]
I have tried to install a few too many java programs in my quest to get ProjectX to work, and I would be happy if I could remove them, is there any chance of being able to do this please
[/QUOTE]

Everything you've installed with Debian .deb packages, are easy to remove.
You just need to know the package name. You can do this using graphical
user interface by starting 'synaptic' (System > Adminstration > Synaptic Package
Manager) and search for installed packages that have java on their description.
You probably know which of those are different JVM's and what you installed
yourself.

other way is to query .deb database manually, for example
```

dpkg -l '*sun*'
apt-cache search java

```

When you find the package you want to remove, you can do on synaptic by
right clicking that package and choose "remove" or manually by doing
```

sudo apt-get remove *package*

```


[QUOTE=keith whitehouse]
My problem lies with a program ProjectX which I now find out comes with its own java so that it needs nothing else to run. In "Windows" when you click the ProjextX.exe file it opens a window and you can see it creating ProjectX. I cannot get it to do this in Ubuntoo
[/QUOTE]

okay, so that .exe is some kind of laucher / installer? There is a .jar file or class
file that the .exe will execute. If you can find what it is, it's trivial task to write
similar launcher for linux environment.

---

### Post by keith whitehouse on 2006-05-26
Hi mlind,

many thanks for all of the information, I will give it a go after dinner.

best regards keith

---

