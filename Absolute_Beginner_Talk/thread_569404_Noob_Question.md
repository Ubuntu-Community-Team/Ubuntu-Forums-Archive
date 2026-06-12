---
title: "Noob Question"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-07
hey,

how do I

Add the following line in /etc/apt/sources.list:

For Feisty (7.04):

deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main

Once I get the terminal command inputed what do I do?

lol thanks

---

### Post by taurus on 2007-10-07
From a terminal, run

```
gksudo gedit /etc/apt/sources.list
```
Now, scroll to the end and add that line to it.  Save it and exit gedit text editor.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by JasonBourneLinux on 2007-10-07
just an update- can i just add URLs to the repository

like surforge ones and get programs such as ndiswrapper

---

### Post by equal on 2007-10-07
> sudo gedit /etc/apt/sources.list

paste that package to the bottom of the file, and save it. Then just enter:

> sudo apt-get update

and everything should be working!

---

### Post by JasonBourneLinux on 2007-10-07
thanks guys!!!

---

### Post by mysticmatrix on 2007-10-07
> **JasonBourneLinux said:**
> thanks guys!!!

GUI ways:

1) Open Softwre Sources in System-->Administration
2) Go to 3rd party tab. Click add soure
3) Paste the required line in dialog box it asks.

Cheers

---

### Post by shae on 2007-10-07
No.  You can only add specially set up repositories.  However, you can probably find a repository for almost anything you would want.

---

### Post by Frak on 2007-10-07
> **JasonBourneLinux said:**
> just an update- can i just add URLs to the repository

like surforge ones and get programs such as ndiswrapper
Only Ubuntu repos, ones that start with deb and have been specified as either an Ubuntu repo, or an Ubuntu/Debian repo.

---

