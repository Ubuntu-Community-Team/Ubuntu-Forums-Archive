---
title: "cant fakeroot java package"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-03-01
Iam a kubuntu breezy user. I tried to install JRE plugin for firefox. I downloaded jre 1.5 package from sun website and ran it to install. But my firefox doesnot recognise the JRE installation. Moreover when i typed about:plugins in firefox address bar it did not show me the JRE plugin. I even tried to apt-get it but it said that the installed version is the new one!!!
```
sriram@Home:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
sun-j2re1.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 174 not upgraded.
sriram@Home:~$  
``` 
So i thought to can convert the bin package into a .deb package by using fakeroot command but since am using kubuntu it didnot recognise that command too. CAn anybody help me with a solution. thnx in advance.

---

### Post by Pragmatist on 2006-03-01
One approach is to create a link to the library file in firefox's plugins directory:
Mine is located here:
/usr/lib/mozilla-firefox/plugins/libjavaplugin.so
It is a symbolic to this file:
/etc/alternatives/firefox-javaplugin.so 

So, do this:
```
sudo updatedb
```
```
locate javaplugin
```
go to your /usr/lib/mozilla-firefox/plugins directory and create the symbolic link:
```
ln -s /etc/alternatives/firefox-javaplugin.so libjavaplugin.so
```

Alternatively, I just noticed that synaptic has a java plugin for firefox! (duh!):
```
sudo synaptic
```
do a search in synaptic for: j2re1.4-mozilla-plugin
install it and see if that helps.

---

