---
title: "compizconfig0 removed, how do I get it back?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Scott.sb87 on 2008-02-29
In an attempt to get "Advanced Settings Manager" to appear for compiz, I unfortunately completely removed compizconfig0.  How do I get it back?  Here are a few things I've tried:

```
supers@supers-laptop:~$ sudo aptitude download compizconfig0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Can't find a package named "compizconfig0"

supers@supers-laptop:~$ sudo aptitude install compizconfig0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig0"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 
```
Any help would be very much appreciated.

Thanks,

Scott

---

### Post by PeterJS on 2008-02-29
The package name for compiz config is:
```

libcompizconfig0

```
And the name of ccsm package is:
```

compizconfig-settings-manager

```

---

### Post by Scott.sb87 on 2008-02-29
> The package name for compiz config is:

```

libcompizconfig0

```
And the name of ccsm package is:

```

compizconfig-settings-manager

```


So it tried those, here is what I got:

```
sudo aptitude install libcompizconfig0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
[COLOR="DarkRed"]No candidate version found for libcompizconfig0[/COLOR]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

sudo aptitude download libcompizconfig0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
[COLOR="DarkRed"]No candidate version found for libcompizconfig0[/COLOR]

sudo aptitude install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
[COLOR="DarkRed"]The following packages are BROKEN:
  python-compizconfig 
[/COLOR]The following NEW packages will be installed:
  compizconfig-settings-manager 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 540kB of archives. After unpacking 3486kB will be used.
The following packages have unmet dependencies:
  python-compizconfig: Depends: libcompizconfig0 which is a virtual package.
Resolving dependencies...
[COLOR="DarkRed"]Unable to resolve dependencies!  Giving up...
Abort.[/COLOR]
 
```


Now what?

---

### Post by owbizi on 2008-02-29
Have you tried apt-get?

---

### Post by PeterJS on 2008-02-29
Here's the package page for it, can you download and install it maually?
[http://packages.ubuntu.com/gutsy/libcompizconfig0](http://packages.ubuntu.com/gutsy/libcompizconfig0)

---

### Post by forrestcupp on 2008-02-29
try doing a 
```
sudo apt-get update
sudo apt-get --reinstall install compizconfig-settings-manager
```
The update may help.

---

### Post by Scott.sb87 on 2008-02-29
> **PeterJS said:**
> Here's the package page for it, can you download and install it maually?
[http://packages.ubuntu.com/gutsy/libcompizconfig0](http://packages.ubuntu.com/gutsy/libcompizconfig0)

That's worked!!! Thanks.  Now my only problem is I don't, for some reason, have any borders around my windows.  Because of that, I can't resize, move, minimize or close any of the windows without using shortcuts.  Any ideas?

---

### Post by Scott.sb87 on 2008-02-29
> **forrestcupp said:**
> try doing a 
```
sudo apt-get update
sudo apt-get --reinstall install compizconfig-settings-manager
```
The update may help.

That got me the advanced windows management, thanks.  But I still have the lack of border problem now.

---

### Post by glennric on 2008-02-29
Type in a terminal
```
gtk-window-decorator --replace &
```
or install emerald and type
```
emerald --replace &
```

---

### Post by PeterJS on 2008-02-29
Looks like you don't have a Window Manager running. So I'd suggest starting metacity just so you have borders to work with, alt+f2, then:
```

metacity --replace

```
Open up CCSM, and check out the window decorator plugin, to make sure it is enabled and the command item is set to
```

emerald --replace

```
Once that's good you can restart compize with, alt+f2, and then:
```

compiz --replace

```

---

### Post by glennric on 2008-02-29
If those things still don't work try 
```
sudo apt-get install --reinstall compiz-gnome
```
then try those other things.

---

### Post by Scott.sb87 on 2008-02-29
Ahh, it works now! Thanks for the help everyone.  Very much appreciated. :)

---

