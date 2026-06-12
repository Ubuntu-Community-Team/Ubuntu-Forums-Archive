---
title: "uninstalling an application"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by nsa_767 on 2005-08-31
Hi there,

I was wondering, if I install a package from source (i.e. I download a .tar.gz), how would I uninstall it? Does it show up in Synaptic?

I know that if I use synaptic to install something, I can very easily uninstall it. The same holds for binary packages (.deb) files downloaded and installed from the web (not through apt-get or synaptic). But what about something I build/install from source?

Any help in this matter will be appreciated.

---

### Post by earobinson on 2005-08-31
im pretty sure the answer is no, unless you compiled it to an rpm then installe it, but if your runing a scrypt to install something then who knows.

---

### Post by kagashe on 2005-08-31
Sometimes the packages installed through install script also have an uninstall script. You can read the help files in the tar.gz.

kagashe

---

### Post by nad on 2005-08-31
To uninstall an application that you built from source, look in the source directory to see if there is a log file of the applications' installed files. You may simply remove these files, provided that they do not satisfy the dependency of any other app.

Any application that is not managed by your package manager ... is not managed.

---

### Post by nsa_767 on 2005-08-31
Thanx for the help guys....

I think I'll try and get a little more experience with Linux before I try and build/compile programs which might not run properly...  :) 

Thanx again

---

### Post by kagashe on 2005-09-01
[QUOTE=nsa_767]Thanx for the help guys....

I think I'll try and get a little more experience with Linux before I try and build/compile programs which might not run properly...  :) 

Thanx again[/QUOTE]I suggest if you want to install any program which does not have .deb package try to get RPM of it and not tar.gz.
Use alien to convert RPM to .deb
Then use dpkg -i debfile to install it.
If you want to remove use dpkg -r debfile

kagashe

---

### Post by A-star on 2005-09-01
[QUOTE=kagashe]I suggest if you want to install any program which does not have .deb package try to get RPM of it and not tar.gz.
Use alien to convert RPM to .deb
Then use dpkg -i debfile to install it.
If you want to remove use dpkg -r debfile
[/QUOTE]

and if you make something from source instead of using "make install" use "checkinstall".
This will make a deb file for you which you can uninstall later.

To install "checkinstall" just do this:
```

sudo apt-get install checkinstall

```

---

### Post by sapo on 2005-09-01
[QUOTE=nsa_767]Hi there,

I was wondering, if I install a package from source (i.e. I download a .tar.gz), how would I uninstall it? Does it show up in Synaptic?

I know that if I use synaptic to install something, I can very easily uninstall it. The same holds for binary packages (.deb) files downloaded and installed from the web (not through apt-get or synaptic). But what about something I build/install from source?

Any help in this matter will be appreciated.[/QUOTE]
 You can unistall it.. its pretty troublesome and kinda dirty but you can..

for example.. you download the software: software.tar.gz

the you install it...

tar xzvf software.tar.gz
./configure
make
sudo make install

ok your software is install.. now to remove it.. you need the source and you need to be in the same folder as you installed it.. and just type:

```
sudo make unistall
```

it will remove your software, but remember.. you CANT delete the source that you used to install.. otherwise the make unistall isnt going to work.

I have a lot of source code here just for that purpose :P

---

### Post by UbuWu on 2005-09-01
Checkinstall, as mentioned above, is the way to go...

---

