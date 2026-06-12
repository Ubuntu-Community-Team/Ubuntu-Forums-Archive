---
title: "Error message after installing package"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by rioja on 2007-11-15
After I install a package using synaptic PM, I get this message;

E: msttcorefonts: subprocess post-installation script returned error exit status 1

What does it mean?

Thanks

---

### Post by Happy_Man on 2007-11-15
It means something went wrong when you tried to install the package msttcorefonts. To fix this, use ```
sudo apt-get -f install
```

---

### Post by rioja on 2007-11-15
Did that and got;
kevin@kevin-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@kevin-desktop:~$ 


Doesn't look fixed?

---

### Post by Happy_Man on 2007-11-16
That's interesting.... it seems the URL for the Microsoft fonts is not showing up for you. 

Try these commands:

```
sudo apt-get remove msttcorefonts
```
```
sudo apt-get clean
```
```
sudo apt-get install msttcorefonts
```

---

### Post by ronmarley1 on 2007-11-16
I also did as suggested above and am still getting the same error.

---

### Post by ronmarley1 on 2007-11-17
I ran the update again and all is well.  Maybe the problem was that I was on campus, and the firewall blocks some parts of sourceforge and not others.

---

