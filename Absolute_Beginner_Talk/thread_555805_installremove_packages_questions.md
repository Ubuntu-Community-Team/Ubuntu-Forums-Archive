---
title: "install/remove packages questions"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-09-20
ok...this is gonna take a min

i am building a phpwiki site with a LAMP server (fiesty). However, the command:

sudo apt-get install phpwiki 

does not give me the latest version of phpwiki (or phpMyadmin), so i decided to download the .bz2 uncompress and install it myself. i downloaded it as a regualr user, so its in that users home directory. then i:

tar -xvjf phpwiki-1.3.14.tar.bz2

that seems good but i dont know how to actually install it. i read somewhere to use the script file within the package. im not exactly sure what/where this script file is. i did try:

./INSTALL

but it didnt work. at that point i remembered that i better remove the old phpwiki before i install the new one, so i:

sudo apt-get remove phpwiki

1. how do i install a package W/O apt-get?
2. if i do NOT use apt-get to install *package1*, can i still use apt-get to uninstall *package1*?
3. what is the wildcard character i can use with the "locate" command

/cheers

BMg

---

### Post by RomeReactor on 2007-09-20
Hi. Does the download contain a readme file? maybe you need to compile it, and for that you would need to install **build-essential**:
```
sudo apt-get install build-essential
```
and the required dependencies for it--which might be resolved by running:
```
sudo apt-get build-dep phpwiki
```
or check the readme file (ife there is one) for dependencies and install them.

Usually you then would need to run:
```
./configure
```
then:
```
make
```
ansd lastly:
```
sudo make install
```

But better read the readme file; it should contain specific instructions.

As for your other questions:
> 1. how do i install a package W/O apt-get?
You either install a **.run**, **.bin**, or **.sh** like so:
```
sudo ./PACKAGE.bin
```
Or compile it.

> if i do NOT use apt-get to install package1, can i still use apt-get to uninstall package1?
Only if you installed it with apt-get or aptitude, I think (or in a graphical environment with Add/Remove, Gdebi or Synaptic).

> what is the wildcard character i can use with the "locate" command
You probably mean the asterisk, *****.

Hope this helps.

---

### Post by forestpixie on 2007-09-20
> if i do NOT use apt-get to install package1, can i still use apt-get to uninstall package1?

if it's a deb I'm fairly sure it turns up in Synaptic (at the least my openoffice is and I did  that after using alien on a rpm) - so I assume apt-get remove would work

---

### Post by Maestro23 on 2007-09-20
Just to tack onto RomeR's excellent post:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by phoenix24x on 2007-09-21
/thanx

---

### Post by hyper_ch on 2007-09-21
as it is "php" I don't think you have to compile it...

I tend to think - as with any other php script - you'll have to run it in a browser if it has a setup routine and if not, you will need to configure it by editing its config.inc.php (or similar) file.

There should be some INSTALL file that will tell you how to set it up.

---

