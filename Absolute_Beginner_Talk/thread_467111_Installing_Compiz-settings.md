---
title: "Installing Compiz-settings"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-07
Hello!!

I am trying to install compiz-settings after installing compiz from synaptic.  I have downloaded the tar file and unpacked it and now I am trying to install it.
It says to type "./autogen.sh --prefix=/usr" and then "make" and then "sudo make install" but already after typing the first thing I get an error message saying:


checking for PACKAGE... configure: error: Package requirements (dbus-1 compiz >= 0.3.3 dbus-glib-1 gconf-2.0 gtk+-2.0 >= 2.0.0) were not met:

No package 'dbus-1' found
No package 'compiz' found
No package 'dbus-glib-1' found 
No package 'gconf-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I am not sure what to do...I checked in synaptic and I have dbus-1 installed for example. 
I am lost!
I am using Ubuntu Feisty on a Compaq R4000 (amd64)

THANKS!

---

### Post by p_quarles on 2007-06-07
Read this:
[http://ubuntuforums.org/showpost.php?p=2191952&postcount=1](http://ubuntuforums.org/showpost.php?p=2191952&postcount=1)

---

### Post by lazyart on 2007-06-07
Compiz is already installed (desktop effects).  How about```
sudo apt-get compiz-manager
```

---

### Post by matteospqr on 2007-06-07
It tells me "invalid operation" when I try and run that command.

---

### Post by matteospqr on 2007-06-07
I installed compiz already from synaptic, isnt there an easy way to install compiz-settings and get it started???

---

### Post by nol1ght on 2007-06-08
try ```
sudo apt-get install compiz-settings
```
and then  ```
sudo compiz-settings
```

---

### Post by kinkdxm on 2007-06-08
> **nol1ght said:**
> try ```
sudo apt-get install compiz-settings
```


:(

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-settings

---

### Post by nol1ght on 2007-06-08
Compiz repository: [http://gandalfn.wordpress.com/compiz-repository/](http://gandalfn.wordpress.com/compiz-repository/)
try this )

---

### Post by matteospqr on 2007-06-08
The thing is that this repository is old gandalf... 
Ubuntu is always unable to connect to it.  On the compiz website there is a .deb file but its for i386 and I have a amd64.  Not quite sure what to do!
:(

---

### Post by PlainShane on 2007-06-11
> **matteospqr said:**
> The thing is that this repository is old gandalf... 
Ubuntu is always unable to connect to it.  On the compiz website there is a .deb file but its for i386 and I have a amd64.  Not quite sure what to do!
:(

I'm in the same boat as you. I have a core2duo.. Can not get the extras working because settings is not working.

---

### Post by antiemptyv on 2007-06-11
> **PlainShane said:**
> I'm in the same boat as you. I have a core2duo.. Can not get the extras working because settings is not working.

same here.  

does anyone know if it is possible for us to use those extra plugins?

---

### Post by antiemptyv on 2007-06-11
oh wait.  actually, yes, we can use them.  i guess we've got to just enable them manually via gconf-editor since there isn't (or i just can't find) an x86_64 compiz-settings deb.  is this right?

---

### Post by PlainShane on 2007-06-11
It is difficult to use gconf-editor if you are relatively new to Linux. I am. I want the feature where when you close a window sparkly magic fire-ish stuff burns it up. There is no way to tell how to enable stuff like that or the windows-off-the-surface cube feature. Scoured the gconf-editor and did not find them but I found snow and such. I turned snow on I thought via gconf-editor and nothing happened...

Guide?

---

### Post by matteospqr on 2007-06-11
People there is a .deb for amd64 for compiz settings.  Its on this site:

[http://ubuntu.moshen.de/dists/feisty/eyecandy/](http://ubuntu.moshen.de/dists/feisty/eyecandy/)

Hope this helps!

---

### Post by PlainShane on 2007-06-12
Wow, thanks. Although most of the options do not seem to stay checked after I enable them... They immediately go back to disabled... Alas, the animation window effects like fire and magic dust are not there.

It did help matteospqr but do you recognize this problem?

---

