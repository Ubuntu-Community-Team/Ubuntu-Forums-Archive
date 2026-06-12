---
title: "Seveas packages"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by johan_dulac on 2007-04-04
Hello,

It should be possible to add all codes etc. from the Seveas website ([http://mirror.ubuntulinux.nl/dists/edgy-seveas/)](http://mirror.ubuntulinux.nl/dists/edgy-seveas/)). I am an absolute beginner and when I read the following I don have the slightest ides what to do.

QUOTE
Seveas' Ubuntu packages
Component all

This is the 'all' metacomponent containing all packages in all components.

You can use apt to download and install the packages. 

Use the following lines in /etc/apt/sources.list and use the command sudo apt-get update to enable downloading from this component.
*How do I add this source?*

Don't forget to read the notice on the frontpage!

deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

UNQUOTE

I know how to open a terminal, but if anyone could explain me exactly what to type in I would appreciate that very much.

Johan Dulac

---

### Post by az on 2007-04-04
Just use synaptic to add a repository.  Select custom and add each line one at a time.  No need to edit the file by hand.

---

### Post by Bachstelze on 2007-04-04
```
sudo -i
echo "deb http://mirror.ubuntulinux.nl edgy-seveas all" >> /etc/apt/sources.list
echo "deb-src http://mirror.ubuntulinux.nl edgy-seveas all" >> /etc/apt/sources.list
apt-get update
exit

```

---

### Post by george29 on 2007-04-04
```
cd /etc/apt
sudo cp sources.list sources.list_backup
sudo nano sources.list

```
type in the lines 
deb....
deb-src...

then exit by pressing [ctrl+X]
save the file - press Y

then type
```
sudo apt-get update
sudo apt-get install (package name that you want to install)
```

---

