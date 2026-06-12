---
title: "Kiba-dock wont uninstall"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-06
how can I remove it. I tried going into seperate folders and doing ```
sudo make uninstall 
```and its a no go.

---

### Post by Perfect Storm on 2008-01-06
You can only do that command, in the source folder after the "make" is done.
If you followed the guide that make you install 4 diffrent things with kiba you need to do the ./configure, make
Thereafter sudo make uninstall.

---

### Post by Fleece Flamingo on 2008-01-06
lol a little to fast for my noob brain :lolflag:

I used this thread [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba)

---

### Post by Perfect Storm on 2008-01-06
Do you still have these folders?

```
cd kiba-dock
```

There should be 4 folders

```
ls -a
```
akamaru
kiba-dock
kiba-plugins
kiba-dbus-plugins

Now entering the first
```
cd akamaru
sudo make uninstall
cd ..
```

Then do the same thing with the others.

If you deleted these folders, you have to do the guide again and instead of running sudo make install run sudo make uninstall.

---

### Post by Fleece Flamingo on 2008-01-06
```
pj@pj-desktop:~$ cd kiba-dock
pj@pj-desktop:~/kiba-dock$ ls -a
.  ..  akamaru  kiba-dbus-plugins  kiba-plugins
pj@pj-desktop:~/kiba-dock$ 


```
Am I missing one?

---

### Post by Perfect Storm on 2008-01-06
It seems you have not compiled kiba-dbus-plugins

---

### Post by Fleece Flamingo on 2008-01-06
So what do I do? I went back and installed the dbus plugins again.

---

### Post by Perfect Storm on 2008-01-06
now you enter each of the 4 folders and do a sudo make uninstall

---

### Post by Fleece Flamingo on 2008-01-06
I do and it doesnt work

---

### Post by Fleece Flamingo on 2008-01-06
So far this is what it looks like ```
pj@pj-desktop:~$ cd kiba-dock
pj@pj-desktop:~/kiba-dock$ ls -a
.  ..  [COLOR="RoyalBlue"]**akamaru  kiba-dbus-plugins  kiba-dock  kiba-plugins**[/COLOR]
pj@pj-desktop:~/kiba-dock$ cd akamaru
pj@pj-desktop:~/kiba-dock/akamaru$ sudo make uninstall cd..
[sudo] password for pj:
Making uninstall in src
make[1]: Entering directory `/home/pj/kiba-dock/akamaru/src'
+ list=libakamaru.la
+ for p in '$list'
++ echo libakamaru.la
++ sed -e 's|^.*/||'
+ p=libakamaru.la
+ echo ' /bin/bash ../libtool --mode=uninstall rm -f '\''/usr/local/lib/libakamaru.la'\'''
 /bin/bash ../libtool --mode=uninstall rm -f '/usr/local/lib/libakamaru.la'
+ /bin/bash ../libtool --mode=uninstall rm -f /usr/local/lib/libakamaru.la
rm -f /usr/local/lib/libakamaru.la /usr/local/lib/libakamaru.so.0.0.0 /usr/local/lib/libakamaru.so.0 /usr/local/lib/libakamaru.so /usr/local/lib/libakamaru.a
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru/src'
Making uninstall in include
make[1]: Entering directory `/home/pj/kiba-dock/akamaru/include'
 rm -f '/usr/local/include/akamaru/akamaru.h'
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/pj/kiba-dock/akamaru'
 rm -f '/usr/local/lib/pkgconfig/akamaru.pc'
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru'
make: *** No rule to make target `cd..'.  Stop.
pj@pj-desktop:~/kiba-dock/akamaru$ 

``` and that folder still exists.

---

### Post by Perfect Storm on 2008-01-06
It's
sudo make uninstall
<enter>
cd ..

---

### Post by Fleece Flamingo on 2008-01-06
I get this and I check my home folder for the akamaru files and they still exist.
```
pj@pj-desktop:~$ cd kiba-dock/akamaru
pj@pj-desktop:~/kiba-dock/akamaru$ sudo make uninstall
Making uninstall in src
make[1]: Entering directory `/home/pj/kiba-dock/akamaru/src'
+ list=libakamaru.la
+ for p in '$list'
++ echo libakamaru.la
++ sed -e 's|^.*/||'
+ p=libakamaru.la
+ echo ' /bin/bash ../libtool --mode=uninstall rm -f '\''/usr/local/lib/libakamaru.la'\'''
 /bin/bash ../libtool --mode=uninstall rm -f '/usr/local/lib/libakamaru.la'
+ /bin/bash ../libtool --mode=uninstall rm -f /usr/local/lib/libakamaru.la
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru/src'
Making uninstall in include
make[1]: Entering directory `/home/pj/kiba-dock/akamaru/include'
 rm -f '/usr/local/include/akamaru/akamaru.h'
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/pj/kiba-dock/akamaru'
 rm -f '/usr/local/lib/pkgconfig/akamaru.pc'
make[1]: Leaving directory `/home/pj/kiba-dock/akamaru'
pj@pj-desktop:~/kiba-dock/akamaru$ cd..

```

---

### Post by Fleece Flamingo on 2008-01-06
and when it comes to the kiba-dock folder I get this ```
/home/pj/kiba-dock/akamaru/include
```

---

### Post by Perfect Storm on 2008-01-06
another option is to use sudo checkinstall to install kiba-dock thereafter you can easely uninstall them via synaptic.
This way you can get rid of them.

---

### Post by jakey21 on 2008-02-05
i have the same problem and it shows that i have it installed but wont let me uninstall it. I used the guide that is posted [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)  i tried searching in add/remove and synaptics and doesnt list it.  i've googled it and results dont work. if theres any other way to get it off that would be great. when i do ls -a it gives me: akamaru  kiba-dbus-plugins  kiba-dock  kiba-plugins. so when i do the uninstall it gives me: jake@ubuntu-jake:~/kiba-dock$ cd akamaru 
jake@ubuntu-jake:~/kiba-dock/akamaru$ sudo make uninstall cd..
Making uninstall in src
make[1]: Entering directory `/home/jake/kiba-dock/akamaru/src'
+ list=libakamaru.la
+ for p in '$list'
++ echo libakamaru.la
++ sed -e 's|^.*/||'
+ p=libakamaru.la
+ echo ' /bin/bash ../libtool --mode=uninstall rm -f '\''/usr/lib64/libakamaru.la'\'''
 /bin/bash ../libtool --mode=uninstall rm -f '/usr/lib64/libakamaru.la'
+ /bin/bash ../libtool --mode=uninstall rm -f /usr/lib64/libakamaru.la
rm -f /usr/lib64/libakamaru.la /usr/lib64/libakamaru.so.0.0.0 /usr/lib64/libakamaru.so.0 /usr/lib64/libakamaru.so /usr/lib64/libakamaru.a
make[1]: Leaving directory `/home/jake/kiba-dock/akamaru/src'
Making uninstall in include
make[1]: Entering directory `/home/jake/kiba-dock/akamaru/include'
 rm -f '/usr/include/akamaru/akamaru.h'
make[1]: Leaving directory `/home/jake/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/jake/kiba-dock/akamaru'
 rm -f '/usr/lib64/pkgconfig/akamaru.pc'
make[1]: Leaving directory `/home/jake/kiba-dock/akamaru'
make: *** No rule to make target `cd..'.  Stop.
jake@ubuntu-jake:~/kiba-dock/akamaru$ sudo make uninstall
make: *** No rule to make target `Makefile.am', needed by `Makefile.in'.  S

i am confused on this whole thing. i just wanted a dock for Ubuntu 7.10 to work. any help will be appreciated thanks.

---

