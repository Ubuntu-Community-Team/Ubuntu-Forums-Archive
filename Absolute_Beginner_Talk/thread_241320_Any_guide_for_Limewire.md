---
title: "Any guide for Limewire?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by MacDonagh on 2006-08-22
I ask if there is any guide to installing Limewire. My problem is that it says that it's archive isn't supported or something.

Any help?

---

### Post by bluenova on 2006-08-22
Why not Frostwire? It's the Limewire open source alternative.

[Frostwire Ubuntu DEB](http://www.frostwire.com/download.php?file=http://mirror1.peercommons.net/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb)

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by Perfect Storm on 2006-08-23
If you saved the Limewire.rpm to your Desktop.

```
sudo aptitude install alien
cd Desktop
sudo alien -i Limewire.rpm

```

---

### Post by cptjaben on 2006-08-23
my advice would be to stop using limewire and try bitorrent instead.

---

### Post by underdog512 on 2006-08-23
Ok here is what you do.

You need to use frostwire because it has a a package that is made for ubuntu and it is the same as limewire.

Before you do anything open up a terminal and the following commands


[SIZE="2"]wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in[/SIZE]

A little window pop up.  Search through there and make sure you install the Java stuff. its what you need to run frostwire

After you have done that....

Go to [http://www.frostwire.com/](http://www.frostwire.com/) and download the package for ubuntu.

after you have downloaded it, you will have to go to the directory in which you installed it and run... 

dpkg --install [*name of package*]

After you have installed it you will get a similar error that you  have been getting from limewire.

Not to worry, simply run the following command.

sudo update-alternatives --config java

select the sun java.


Frostwire should run now

---

