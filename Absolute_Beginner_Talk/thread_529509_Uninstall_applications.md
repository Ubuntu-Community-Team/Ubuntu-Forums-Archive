---
title: "Uninstall applications"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by fickendichdu on 2007-08-19
I have installed some applications using ./configure make and make install.  I do not use them anymore or just don't like them.  How can I uninstall them?  Also how do you uninstall programs that are in .deb format?

---

### Post by kidcharles on 2007-08-19
Typically you can use the command 'make uninstall' to uninstall.

---

### Post by schorsch on 2007-08-19
If you still have the directory in which you compiled the appilcations please change into them and try
```
make uninstall
```
If the code is properly written this will uninstall the applications ... sometimes. Otherwise you  will have to search for the compiled files by yourself.
You can install the package "checkinstall" and instead of compiling in the last step with "sudo make install" you can type "sudo checkinstall"; this will track the installation process. But only for packages you will compile in the future .... it will not help you to solve your actual problem.

---

### Post by kidcharles on 2007-08-19
For .deb files, they can easily be removed, assuming they were installed by the synaptic program (which can be done either with System->Administration->Synaptic Package Manager or using the command line with 'apt-get' or 'dpkg'). Under the synaptic GUI you can simply search for them and mark them for 'removal' or 'complete removal' (the latter will delete absolutely everything, including configuration files.) On the command line you can type 'apt-get remove <package name>'.

---

### Post by fickendichdu on 2007-08-19
The deb files where from getdeb.net and installed with gDebi installer.

---

### Post by fickendichdu on 2007-08-19
> **schorsch said:**
> If you still have the directory in which you compiled the appilcations please change into them and try
```
make uninstall
```
If the code is properly written this will uninstall the applications ... sometimes. Otherwise you  will have to search for the compiled files by yourself.
You can install the package "checkinstall" and instead of compiling in the last step with "sudo make install" you can type "sudo checkinstall"; this will track the installation process. But only for packages you will compile in the future .... it will not help you to solve your actual problem.

```
make uninstall
```

That did work and I will try the checkinstall in the future and see how that works.  Thanks for the help.

---

### Post by AdotB on 2007-08-19
Someone should make a program or script that can create and uninstall script and maybe store it somewhere like ~/.uninstall.  I like to save space, so i usually delete the source directory when I'm done.

I'd like to do it, but I'm not skilled enough in that area. I would like to hear if anyone has any ideas though.

---

### Post by mcduck on 2007-08-19
> **AdotB said:**
> Someone should make a program or script that can create and uninstall script and maybe store it somewhere like ~/.uninstall.  I like to save space, so i usually delete the source directory when I'm done.

I'd like to do it, but I'm not skilled enough in that area. I would like to hear if anyone has any ideas though.

Checkinstall pretty much solves the problem in a better way. It creates a .deb package from your compiled program and then installs it with the package manager. This way you don't need to keep the sources or any installer script, the program will show in Synaptic and can be removed just like any other package in your system.. :)

You can even keep the .deb package if you want to install the same program on other machines, but you'll have to install possible dependencies yourself as checkinstall doesn't add dependency information to packages.

---

### Post by crjackson on 2007-08-22
> **fickendichdu said:**
> The deb files where from getdeb.net and installed with gDebi installer.

Go to system>administration>synaptic package manager>status>installed>find you app and mark it for removal.

---

### Post by AceofSpades19 on 2007-08-22
sudo apt-get remove <insertnameofprogramhere>

---

