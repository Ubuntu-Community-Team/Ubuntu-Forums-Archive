---
title: "Possible to do this in apt-get ??"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-06-02
I want to save a list of all the packages I have installed on my system.

Then if I have to re-install my feisty I can run a script which scans through the list and installs the packages which haven't already been installed from the default install.

First off is there a list anywhere which I can use that contains all installed packages? 

second, is there an existing script or way to 'restore' the packages I had installed ?

Thanks

---

### Post by indytim on 2007-06-02
This might help a bit.

To get a list of installed apps and have the list written to your home directory

```
dpkg --get-selections > installed-software
```

And if you want to re-install from the same list:

```
dpkg --set-selections < installed-software

followed by

dselect


```

Hope this helps,

IndyTim

---

### Post by PetePete on 2007-06-02
thanks, just what i needed :)

presumably i'd select option 3 (Install) within dselect to install the new packages ?

---

### Post by Chilli Bob on 2007-06-02
Have you tried [APTonCD?]("http://aptoncd.sourceforge.net/")

---

### Post by PetePete on 2007-06-03
APTonCD looks perfect, thank you thank you thank you!!!

edit:
although it requires lots of dependencies which i dont have.
think i'll use the CLI trick

---

### Post by zvacet on 2007-06-03
> although it requires lots of dependencies which i dont have

It is in synaptic(Adept in you case).Just install it.It is good tool.

---

