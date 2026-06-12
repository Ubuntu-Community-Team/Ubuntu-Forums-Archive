---
title: "VirtualBox Error"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by bbharatsony on 2007-10-11
Whenever I try to install VirtualBox GDebi Package Installer says Error:Dependency not satisfiable: libqt3-mt. Can someone help me with this.

---

### Post by skymera on 2007-10-11
install it from the repos :wink:

sudo apt-get install virtualbox

or summin, i cant check im in XP atm

---

### Post by bbharatsony on 2007-10-11
The terminal says E: Couldn't find package virtualbox

---

### Post by forestpixie on 2007-10-11
it's virtualbox-ose

```
sudo apt-get install virtualbox-ose
```

you can search in apt quite easily, which is how I found this - didn't know it was there either :)

to search

```
sudo apt-cache search *nameofpackage*
```

---

### Post by bbharatsony on 2007-10-11
Can someone just tell me how to fix the dependency problem at the very top.

---

### Post by forestpixie on 2007-10-11
well just try installing it in terminal

sudo apt-get install nameofpackage

---

### Post by bodhi.zazen on 2007-10-11
> **bbharatsony said:**
> Can someone just tell me how to fix the dependency problem at the very top.

First try, from a terminal, ```
sudo apt-get install -f
```

Then re-install Virtualbox.

If the fails remove it with this command:```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

And install it like this :

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

^^ From the innotek repo

---

### Post by Dr Small on 2007-10-11
[http://ubuntuforums.org/showpost.php?p=3496809&postcount=2](http://ubuntuforums.org/showpost.php?p=3496809&postcount=2)

---

### Post by cowkiller on 2007-10-11
> **bbharatsony said:**
> Whenever I try to install VirtualBox GDebi Package Installer says Error:Dependency not satisfiable: libqt3-mt. Can someone help me with this.

You just have to search for the libqt3-mt library in synaptic package manager and install it, and do so if any other dependency problem comes up

---

### Post by bbharatsony on 2007-10-12
I have already installed the libqt3-mt dependency and still have the same problem.

---

### Post by bbharatsony on 2007-10-12
I use a proxy, so would I be able to use the terminal method?

---

### Post by bodhi.zazen on 2007-10-12
> **bbharatsony said:**
> I use a proxy, so would I be able to use the terminal method?

As far as I know the fact that you use a proxy means you have to configure the proxy.

Other then that I do not see how using a proxy would change anything.

---

