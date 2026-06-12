---
title: "[SOLVED] Installing aMSN and Azureus"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Jet8225 on 2007-12-13
Every time I try to install it form Add/remove program I get that it conflicts with another installed software, so I removed the standard IM that came with the OS. I tried it again and got the same thing, then I try it with the terminal and I get this:
```
The following packages are BROKEN:
  amsn tcltls 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3520kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 which is a virtual package.
        Depends: tk8.4 which is a virtual package.
  tcltls: Depends: tcl8.3 which is a virtual package. or
                   tcl8.4 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

And when I try to install azureus I get the same thing as aMSN and this:
```
Keep the following packages at their current version:
azureus [Not Installed]
icedtea-java7-bin [Not Installed]
icedtea-java7-jre [Not Installed]
libswt3.2-gtk-gcj [Not Installed]
libswt3.2-gtk-java [Not Installed]

Score is -9841

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 
```

Please help me with this.

---

### Post by spiderbatdad on 2007-12-13
those dependencies are other libraries and packages that must also be installed before you can run the programs you want. Most of them are probably in synaptic. Or, can be found with google. You may be able to google amsn and azereus and find .deb packages. these will include the dependencies and can be installed from your desktop with a click of the mouse

[http://www.softonic.com/s/amsn.deb:linux](http://www.softonic.com/s/amsn.deb:linux)

---

### Post by Jet8225 on 2007-12-13
Thanks!

---

