---
title: "Synaptic Error, Please help. thanks"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Arghhh haha on 2007-09-18
Hi there, just installed Ubuntu 7.04, i think its really cool, although I wanted to show my friend what it looked like so i tryed to install a screen recorder, but it didnt work, so i just forgot about it and carried on browsing the new things available on this OS, just as i read about Compiz Fusion i decided to give it a go to find that i couldn't run the Synaptic package manager.

The error i get:

E: The package recordmydesktop needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have done a few searches to see what kind of solutions there are for this sort of problem, and tryed what a few members suggested, to no avail. So here i am asking you all :-D

---

### Post by Arghhh haha on 2007-09-18
is this an uncommon problem or does nobody here know how to solve this ?

---

### Post by angryfirelord on 2007-09-18
Open a terminal and post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by Gremlinzzz on 2007-09-18
sudo apt-get autoremove recordmydesktop

---

### Post by Arghhh haha on 2007-09-18
> **Gremlinzzz said:**
> sudo apt-get autoremove recordmydesktop
sudo apt-get autoremove recordmydesktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package recordmydesktop needs to be reinstalled, but I can't find an archive for it.

---

### Post by splintercellguy on 2007-09-18
Try sudo dpkg --remove --force-remove-reinstreq recordmydesktop.

---

### Post by schorsch on 2007-09-18
```
sudo dpkg --configure --force-remove-reinstreq recordmydesktop
```

---

### Post by Arghhh haha on 2007-09-18
> **splintercellguy said:**
> Try sudo dpkg --remove --force-remove-reinstreq recordmydesktop.

thanks alot thats done the trick, thanks:-D

---

### Post by Arghhh haha on 2007-09-18
> **schorsch said:**
> ```
sudo dpkg --configure --force-remove-reinstreq recordmydesktop
```

:-D thanks

---

