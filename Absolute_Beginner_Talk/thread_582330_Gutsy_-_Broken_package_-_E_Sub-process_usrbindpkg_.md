---
title: "Gutsy - Broken package - E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-19
After upgrading to Gutsy, I got Synaptic error:
You have 1 broken package on your system!
Use the "Broken" filter to locate it.

So, I find that it is the "mono-xsp" package.

I cannot remove or upgrade this package.  Synaptic displays:
E: mono-xsp: subprocess pre-removal script returned error exit status 2

So, I 

$  sudo apt-get remove --purge mono-xsp

and got:

E: Sub-process /usr/bin/dpkg returned an error code (1)


Help -- thanks

Carl

---

### Post by Pumalite on 2007-10-19
Try:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by cwmoser on 2007-10-19
Tried:
sudo dpkg --remove --force-remove-reinstreq mono-xsp

... no help.

Any other suggestions?

Thanks

Carl

---

### Post by DalaiDakkar on 2007-10-19
Hi, 

While upgrading to gutsy I've got this error :S can anyone help me please??
[http://dakkar.tk/terror.jpg](http://dakkar.tk/terror.jpg)

gtk-update-icon-cache: error while loading shared libraries: libgdk_pixbuf-o.0: cannot open shared objet file: no such file or directory
Error where encountered while processing:
gnome-themes

already tried apt-get reconfigure gnome-themes,  the error is the same

please help, thanks a lot

--------------UPDATE-------------------
My problem was fixed with this steps

No, don't delete /usr/lib/libgdk_pixbuf-2.0.so.0... You definetely need that! You can get it back by doing apt-get --reinstall install libgtk2.0-0.

Then run: ldd /usr/lib/libgdk_pixbuf-2.0.so.0 and it will list all libraries that it's trying to load. Look for /usr/local/lib/<<Some file>> the local part is key as this is where most make install's put libraries. Any file in /usr/local/lib is in your way and I suggest moving it somewhere else not deleting it.

Thanks to jalbrant for the help
-------------------------------------------

---

### Post by cacimar on 2007-10-25
bug:
[https://bugs.launchpad.net/ubuntu/+source/xsp/+bug/154992](https://bugs.launchpad.net/ubuntu/+source/xsp/+bug/154992)

---

### Post by cacimar on 2007-10-25
remove as much mono-xsp versions and base as you can using synaptic, then
sudo apt-get -f install mono-xsp-base=1.2.1-1ubuntu1

---

### Post by cwmoser on 2007-10-26
Running that command gives a "was not found" error:


klaatu:~$ sudo apt-get -f install mono-xsp-base=1.2.1-1ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.2.1-1ubuntu1' for 'mono-xsp-base' was not found

klaatu:~$ 


Carl

---

