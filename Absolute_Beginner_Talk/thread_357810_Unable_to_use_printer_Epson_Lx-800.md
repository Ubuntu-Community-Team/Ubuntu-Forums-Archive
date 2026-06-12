---
title: "Unable to use printer Epson Lx-800"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by weapon-x on 2007-02-10
hi,I have a dot matrix printer Epson Lx-800,tried to use it on ubuntu but i didn't find driver.
the Lx- 850 is avaliable on the system ,i m using ubuntu 6.10 i tried to use that driver but my printer start printing something crap.......

Can somebody  help me to find the driver for the linux .....  :popcorn:

---

### Post by Jussi01 on 2007-02-10
there is a driver available here: [http://www.linuxprinting.org/show_driver.cgi?driver=omni](http://www.linuxprinting.org/show_driver.cgi?driver=omni) I havent looked at it much other than that, sorry.

---

### Post by weapon-x on 2007-02-12
i have downloaded the driver pack name **omni** but i not able to install it . Please help me..

---

### Post by seshomaru samma on 2007-02-12
I think the driver might be an rpm ( a package for Red Hat Linux)
if it is you need to install a programme called alien first
In a terminal paste this line:
```
sudo apt-get install alien

```
after it is installed than you can install the driver with this command :
```
sudo alien -i /path/to/package/package_name.rpm
```
notice: you need to replace the /path/to/package part with the location of the driver , so if you downloaded it to your desktop then it would probably be /home/weaponx/Desktop (that is if your user name is 'weaponx', also pay attention to upper and lower case letters)
the package name should be replaced with the actual package name ,probably omni.rpm
it might look like this :
> sudo alien -i /home/weaponx/Desktop/omni.rpm

if its not an rpm ,read [this ]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by weapon-x on 2007-02-12
I have done all as u said.But still i m not able to find my Printer Driver in the driver list..:confused:

---

### Post by seshomaru samma on 2007-02-13
what do you mean ? which driver list?

---

### Post by weapon-x on 2007-02-13
> **seshomaru samma said:**
> what do you mean ? which driver list?



this list when show up in installing the printer (see the image attachment )

---

### Post by seshomaru samma on 2007-02-14
I see.
Not sure ,but maybe you can try downloading the OmniEpsonVendor from :[http://sourceforge.net/project/showfiles.php?group_id=18713](http://sourceforge.net/project/showfiles.php?group_id=18713)
this is a tarball, installing  it is like this :
you probably need to untar it ,right-click on it and choose 'extract here'
then open a terminal , cd to the directory where you put the driver , so if its on the desktop you go :
```
cd /home/waeponx/Desktop
```
then 
```
./configure
```
then
```
make
```
then
```
sudo checkinstall
```

if you get an error it's probably because you need the *build-essential* package which you can get from synaptic

---

### Post by weapon-x on 2007-05-09
when i extrcted OmniEpsonVendor-0.9.2.tar.gz it contains ------
1..Epson.PDC (folder)

2...Makefile.am (file)

Epson.PDC contains... these files
/libsc20s.so
/libsc40s.so
/libsc60s.so
/libsc70s.so
/libsc80s.so
/libsc480.so
/libsc580.so
/libsc680_777.so
/libsc880.so
/libsc980.so
/Makefile.am
/OmniEpsonBlitter.cpp
/Readme.Epson.Kowa.License

./configure is not working.....


Help me please..

---

