---
title: "setting the path, sun java"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-04-26
Hi,
Right I ve been trying to install sun's java. I ve got it installed but I cant set seem to set the path properly. 

I used this guide to install java and I downloaded the bin file not the rpm.
[http://www.dougsparling.com/comp/howto/linux_java.html](http://www.dougsparling.com/comp/howto/linux_java.html)

When I type 
> 
sudo update-alternatives --config java


I get:
> 
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

There is no option for sun java.

I typed this at the console to set the path:
> 
export PATH=$PATH:/usr/java/jdk1.5.0_06/bin  

(this is the correct directory for my java install)

when I type "env"

the path comes up as :
> 
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/java/jdk1.5.0_06/


but the java bit disappears after a restart.

I really need to install sun's java to use something else (jack agent development software).

thanks for any help!

---

### Post by hw-tph on 2006-04-26
In order for you to use update-alternatives to set java options you need to install Java properly the Debian way. This is in fact very easy nowadays. Make sure you have multiverse enabled and then **apt-get install fakeroot java-package**. Download the Sun java .bin file (not the rpm!) and type **fakeroot make-jpkg ${name-of-downloaded-java-package}.bin**. This will create a .deb file for the Java package. Install it using **dpkg -i ${filename}**. Then you can use update-alternatives to set java vm, compiler and man pages.


Håkan

---

### Post by bplus on 2006-04-26
thankyou, that worked a treat!
Just out of interest does everything have to be installed as a debian package in ubuntu?

---

### Post by hw-tph on 2006-04-26
Not really. Most things can be tricked into working but a few things - like Sun's Java - is easiest to install as debs since you can use the Debian tools (like update-alternatives) to configure them. Home built kernels can be made into debs by using make-kpkg (package name is kernel-package), so when a new kernel is installed, it is automatically added to the Grub menu and so on.


Håkan

---

