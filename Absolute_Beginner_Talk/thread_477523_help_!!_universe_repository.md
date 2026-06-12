---
title: "help !! universe repository"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-18
my universe repository is nbot showing up hence i am not able to load beryl it shows this

```
pardesi@pardesi-desktop:~$ sudo aptitude install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for beryl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by Griffiss on 2007-06-18
Have you enabled the universe repository in synaptic?

system>administration>synaptic>settings>repositories

---

### Post by irish_flu on 2007-06-18
Here's how you enable the Unuverse Repositories:

Fire up Synaptic Package Manager (from your "Administration" menu).

Click "Settings", then "repositories".

Check the box next to whichever repositories you want.

Click Close.

You're done!

---

### Post by haricharan on 2007-06-18
if its on feisty 
```
gksudo gedit /etc/apt/sources.list
```
Add the following lines to the end of the file
```
## BERYL PROJECT
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
```

---

