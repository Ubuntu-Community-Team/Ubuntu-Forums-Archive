---
title: "building .deb package, some problems in"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by munna_dude on 2007-09-08
hi all
am building the .deb package for my application...
i have a problem...
i would like to use /usr/lib files.... to read and write...
for that i have to give the permission to that folder called /usr/lib/munna

this should be done at installing the .deb package.
where should and what should i write the command to give the permission...

previously i solved this in fedora7 by giving %attr(0777, root, root) <filename> in the spec file ..

but in ubuntu i dont know where and what give like the fedora..

please help me 

thank you in advance

---

### Post by az on 2007-09-08
I don't think it's whitin policy to install a file in /usr/lib with 777 permissions.

Does this document help:
[http://www.debian.org/doc/debian-policy/ch-files.html#s10.9](http://www.debian.org/doc/debian-policy/ch-files.html#s10.9)

---

### Post by munna_dude on 2007-09-10
> **az said:**
> I don't think it's whitin policy to install a file in /usr/lib with 777 permissions.

Does this document help:
[http://www.debian.org/doc/debian-policy/ch-files.html#s10.9](http://www.debian.org/doc/debian-policy/ch-files.html#s10.9)

sorry.. 
i am not getting solution with the link..
i would like to do this at the time of installing .deb package.
is there any script or to include file in , while creating the .deb package
chmod 0777 /usr/lib/munna/munna.txt


please help me 

thank you in advance

---

### Post by Frak on 2007-09-10
644 permissions.

---

### Post by munna_dude on 2007-09-10
> **Frak said:**
> 644 permissions.


hi thank you for your quick replay..
not 644 permission .. am asking about
i would like to do this at the time of installing .deb package.
is there any script or to include file in , while creating the .deb package
chmod 0777 /usr/lib/munna/munna.txt

please help me 

thank you in advance

---

### Post by capink on 2007-09-10
This can be done using postinst script. Just make a script that contain the commands you wish to run and name it postinst. This will run after the package is copied to the filesystem. The location of the postinst file  depends on the method you are using to build the package. If you are using dpkg-buildpackage -rfakeroot, the location of the postinst script will be debian/postinst. If you are using the dpkg -b the location will be DEBIAN/postinst.

---

### Post by munna_dude on 2007-09-10
yes. i did what u said..
i wrote this in postinst file 
chmod 0777 /usr/lib/munna/
but it saying some errors

> 
munna@munna-desktop:~/Desktop$ sudo dpkg -i munna-4.0.0.0.deb
Selecting previously deselected package munna.
(Reading database ... 110829 files and directories currently installed.)
Unpacking munna (from munna-4.0.0.0.deb) ...
Setting up munna (3.0.0-0) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing munna (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 munna
munna@munna-desktop:~/Desktop$


please help me 

thank you in advamce

---

### Post by capink on 2007-09-10
Can you upload the package for me to examine. If not, at least post the postinst script.

---

### Post by munna_dude on 2007-09-10
> **capink said:**
> Can you upload the package for me to examine. If not, at least post the postinst script.
this is the postinst script
```

#!/bin/sh
chmod 0777 /usr/lib/munna/munna.txt

```

this code is not effecting to change the permission..

please help me 

thank you in advance

---

### Post by capink on 2007-09-10
I've made a package that contain the same file and postinst, it is working for me. I don't know what went wrong for you. Maybe your postinst does not have proper permissions, chmod it to 0755. I forgot to mention that. If that is not your problem, please upload the package so I can examine it.

---

### Post by munna_dude on 2007-09-11
> **capink said:**
> I've made a package that contain the same file and postinst, it is working for me. I don't know what went wrong for you. Maybe your postinst does not have proper permissions, chmod it to 0755. I forgot to mention that. If that is not your problem, please upload the package so I can examine it.

i did the same but no use.. 
i placed this postinst script in DEBIAN folder is it correct..
i have a lot of code.. so, the package is heavy weight, sorry for this.

and also the problem with the permissions for 
```

#!/bin/sh
chmod 0777 /usr/lib/firefox/greprefs/

```

please help me 

thank you i advance

---

### Post by capink on 2007-09-11
OK. Let us examine and repackage the deb as follows:

```
mkdir -p ~/test/DEBIAN
```

```
dpkg --control /path/to/the/package.deb ~/test/DEBIAN
```

now you should find the control file and the postinst file in the ~/test/DEBIAN directory. If the postinst is not present, place it there.

```
chmod 755 ~/test/DEBIAN/postinst
```

This will make sure that the postinst file has correct permissions.

Now will make sure that files and permissions are OK:

```

ls -al ~/test/DEBIAN
```

Note: Please post the output of this command

```
dpkg --extract /path/to/the/package.deb ~/test
```

This should extract the contents of the package to the directory ~/test

```
sudo chown -R root.root ~/test
```

```
dpkg -b ~/test ~/packagename.deb
```

This will repackage a new debian package in your home directory.

---

### Post by munna_dude on 2007-09-11
awesome..
thank you verymuch...
i have another problem...
is there any way to install the files in $HOME path..

if i install the .deb package all files must be installed in $HOME


please help me 

thank you in advance

---

### Post by capink on 2007-09-11
The Debian package install with root privileges, so any mention of $HOME in any of the hook scripts of the package will point to the root home directory which is /root. I don't know of a way to install the package to a specific user directory. Sorry.

---

### Post by munna_dude on 2007-09-11
> **capink said:**
> The Debian package install with root privileges, so any mention of $HOME in any of the hook scripts of the package will point to the root home directory which is /root. I don't know of a way to install the package to a specific user directory. Sorry.

coz, i installing the packege file in various folders..
like /usr/lib
/usr/bin/
/usr/local/share 
etc...

while removing the package some files are not removing..
something in /usr/lib and /usr/local/share ..etc.

---

### Post by capink on 2007-09-11
Any files hardcoded into the package (i.e not created by the package scipts) should be removed when uninstalling. Sometimes some directories remain on the system if they contain a file not belonging to the package (i.e created by the user after the install).

---

### Post by munna_dude on 2007-09-11
> **capink said:**
> Any files hardcoded into the package (i.e not created by the package scipts) should be removed when uninstalling. Sometimes some directories remain on the system if they contain a file not belonging to the package (i.e created by the user after the install).

hi i have another problem..
flash player working with mozilla
but not with firefox...
both have the flash pluggins.
i dont understand whats happening.

i did this..
i replace the /usr/lib/firefox/greprefs/all.js
with
/usr/lib/mozilla-1.7.8/greprefs/all.js

by this flash player working fine...
but with the mozilla all.js , all bookmarks are gone.

what the deference in the both all.js..

is there any script to change in firefox all.js..

please help me

thank you in advance

---

### Post by capink on 2007-09-11
The two files required for flash to work with firefox are

/usr/lib/firefox/plugins/flashplayer.xpt
/usr/lib/firefox/plugins/libflashplayer.so

Both files are supplied by the package flashplugin-nonfree

```
sudo apt-get install flashplugin-nonfree
```

Remember that you have to enable universe repositories first

---

### Post by munna_dude on 2007-09-12
> **capink said:**
> The two files required for flash to work with firefox are

/usr/lib/firefox/plugins/flashplayer.xpt
/usr/lib/firefox/plugins/libflashplayer.so

Both files are supplied by the package flashplugin-nonfree

```
sudo apt-get install flashplugin-nonfree
```

Remember that you have to enable universe repositories first
yes i already installed the plugins..
actually  iam using internet tv. with flash player..
for this am including the firefox libraries...
i.e. libgtkembedmoz and xpcom.so
with this flash player maximising not working..

if i ran the same link(of tv ) in firefox browser it is working file ..
but not working in internet tv...

if i use mozilla ".so" files internet tv working fine..

then i thought some days for this firefox ".so" .
i got the solution for maximising window... like this
by replacing mozilla->all.js file in firefox.

maximising of internet tv working...

but the process which i did it is wrong..
i dont wanna replace the all.js

what to do for this...

sorry for this lengthy post...

please help me 

thank you in advance

---

### Post by capink on 2007-09-12
Sorry. I don't have an answer for that. Hope someone will help you.

---

### Post by munna_dude on 2007-09-13
> **capink said:**
> Sorry. I don't have an answer for that. Hope someone will help you.

thank you for ur kind replay..

hi all
is there anybudt to help me 
regarding all.js..

than you in advance

---

