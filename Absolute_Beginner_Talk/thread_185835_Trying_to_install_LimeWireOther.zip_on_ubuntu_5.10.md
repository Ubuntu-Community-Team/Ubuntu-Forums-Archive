---
title: "Trying to install LimeWireOther.zip on ubuntu 5.10"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by randell6564 on 2006-06-01
Hello!

Im using ubuntu 5.10 breezy.

I have a LimewireOther.zip file sitting in my home folder.

Can someone please provide a link or help on how in the heck to install it?

---

### Post by Rackerz on 2006-06-01
I'd get the LimeWireLinux.rpm file. After you've downloaded the RPM type this in the terminal;

sudo apt-get install alien
cd (path to where the rpm file is located)
sudo alien LimeWireLinux.rpm (or whatever the rpm is called)
sudo dpkg-i LimeWireLinux.deb (or whatever the generated file is named).

Regards

---

### Post by %hMa@?b&lt;C on 2006-06-01
Well, i would use Frostwire.  TO install frostwire do the following

```
wget http://www.frostwire.com/download.php?file=http://www.wedoit4you.com/frostwire/4.10.9/FrostWire-4.10.9-2.i586.deb
```

and then 

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

then to run, go to APPLICATIONS>INTERNET>FROSTWIRE
or from terminal type 
```
frostwire
```

---

