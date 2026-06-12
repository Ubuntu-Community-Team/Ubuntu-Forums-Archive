---
title: "installing from terminal"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-20
hey,

Whenever I try to download something from the terminal say for example beryl, if I insert the following command in my gutsy terminal:

sudo apt-get install beryl

it always says something like:

E: Couldn't find package beryl

Why is that?
In fiesty installation from terminal used to work fine.

---

### Post by Linux_Man on 2007-10-20
Well, first off, there IS no beryl anymore, because Beryl was a fork of Compiz, and Compiz and Beryl merged, Compiz-Fusion IS beryl, also, do you have the Universe and Multiverse repositories enabled?

---

### Post by limac on 2007-10-20
do u mean the one I have to activate fron software sources?

---

### Post by Linux_Man on 2007-10-20
Yep, just activate the Universe and Multiverse repositories and you should be able to install anything you want (Although what I said in my previous post about beryl still is true)

---

### Post by R.Bucky on 2007-10-20
I had the same problem. go to System > Administration > Software Sources and enable or check the top four boxes. Then, try installing from terminal or the Synaptic Package Manager and see how many more software packages are available.

---

### Post by Linux_Man on 2007-10-20
You also might want to do sudo apt-get update afterwards, although I think after changing software sources Ubuntu does that automaticly

---

### Post by rocknrolf77 on 2007-10-20
If you want to search for packages you can do a ```
apt-cache search "package name"
```

---

### Post by R.Bucky on 2007-10-20
Great thought - thanxs Linux_man

---

### Post by limac on 2007-10-20
even if I enable the universe and the multiverse and then try to install from the terminal it is showing the sam error message

---

### Post by Linux_Man on 2007-10-20
Are you connected to the internet? Also the package you have may be not available for example, beryl is NOT in the Gusty repositories, make sure that it is one that is in the repositories, also try sudo apt-get update to make sure that apt-get is synchronized with your software sources.

---

### Post by R.Bucky on 2007-10-20
When I installed Gutsy I had to disable Networking on my computer because the repositories were swamped. Right-click the network icon in the top right to see if you are connected. 

Also, try a good ole fashioned ```
ping www.google.com
```
and see if you are getting a connection.

Try installing something that IS available in Terminal like ```
sudo apt-get install links
```

---

