---
title: "Hoe do I install a tar package with synapic"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-04-14
Hello!

When I have downloaded a new program, a tar.gz file, how do I do to intall it with synapic?

I have tried to "add a downloaded package" but I can´t select the package

Please help!

---

### Post by Legionox on 2007-04-14
You most likely can't install the tar.gz file with synaptic, you'll need to install from source, if you could tell me which program it is I could give you step by step instructions on how to install it.

---

### Post by xopher on 2007-04-14
You can't, synaptic is specifically for .deb's, and handling repositories.

You probably need to compile the tar package manually too. If you really want to do this, I'd recommend **checkinstall**, it creates a deb of the app, and makes it easy to remove/upgrade.

The procedure would be:


```
sudo apt-get install checkinstall
```

```
cd /the/place/where/you've/extracted/the/tar/
```

```
./configure
```

```
make
```

```
sudo checkinstall
```

It'll prompt you for some things, and then you should have the deb ready and installed.

For being able to './configure' and 'make', you need all the dependencies installed for the app though. So it might be easier just to search for a prebuilt version of it.

What app is it anyway?

---

### Post by bashologist on 2007-04-14
Yea, a tar.gz file is an archive containing many files. Synaptic shouldn't be able to use these.

You can extract the files with:
```
tar -xvvzf <filename>.tar.gz
```

Maybe someone can help you but we'll need more information like, what's the program, filename, files in the archive, etc.

---

### Post by jonttix on 2007-04-14
The program is Scilab!

---

### Post by Legionox on 2007-04-21
Ok, I just install Scilab myself and got it right
Make sure you have multiverse repo's enabled (System->Administration->Software Sources, 'Software restricted by copyright and legal issues (multiverse)' (tick to the left of these words))
Open up a Terminal window (Applications->Accessories->Terminal)
Type in ```
sudo apt-get -y install scilab
```
After the installation has finished you can start Scilab by typing ```
scilab
``` into a Termianl Window:KS
NB: I don't even have a clue what Scilab is or what its for!

---

