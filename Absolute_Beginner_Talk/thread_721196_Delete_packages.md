---
title: "Delete packages?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by mrfraser89 on 2008-03-11
So if I download something using the Add/Remove program section, then I uninstall it, the package is still stored on my computer.

How do I delete these files (say, Nexuiz for example).

---

### Post by jken146 on 2008-03-11
```
sudo apt-get clean
``` will delete everything from /var/cache/apt/archives.  If you want to delete a specific individual package, go there and do it yourself.

---

### Post by NightwishFan on 2008-03-11
To avoid this uninstall packages with complete removal in synaptic package manager.
I believe:
```
sudo apt-get purge packagename
```
In terminal window does the same thing.

---

### Post by mrfraser89 on 2008-03-11
Much appreciated, learning so quickly with Ubuntu :D

EDIT - sudo apt-get remove

what does that command do?

(How do I use code tags?)

---

### Post by jan quark on 2008-03-11
when you want your code be displayed as 
```
code
```

use the # sign when you write your message

[sudo:]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29") gives you super user right

apt-get: package manager ( see ```
man apt-get
``` in terminal, it will bring you to a manual of the command, you can quit the manual with q)

remove: guess what :)

---

### Post by hyper_ch on 2008-03-11
to show some text as
```

code

```
wrap that that piese of code around [noparse]```
code
```[/noparse] tags...

Remove will uninstall the packages from the system but it will keep the downloaded .deb file(s) and it will also keep the config files for it. Use the purge option to remove with the configs and the clean one to also delete the .deb file.

---

### Post by vishzilla on 2008-03-11
```
sudo apt-get autoremove *packagename*
``` will remove the entire package including the files which the package depends on and are no longer in use

---

