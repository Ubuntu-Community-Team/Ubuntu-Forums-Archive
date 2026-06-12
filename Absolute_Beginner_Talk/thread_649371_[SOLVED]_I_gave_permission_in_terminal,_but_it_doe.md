---
title: "[SOLVED] I gave permission in terminal, but it doesn't care..."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
```
brandon@brandon-laptop:~$ !/bin/bash
bash: !/bin/bash: event not found
brandon@brandon-laptop:~$ sudo apt-get install compiz-bcop compiz-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libstartup-notification0-dev
The following NEW packages will be installed:
  compiz-bcop compiz-dev libstartup-notification0-dev
0 upgraded, 3 newly installed, 0 to remove and 17 not upgraded.
Need to get 92.1kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

```

When it said "Do you want to continue [Y/n]?

I typed in Y

and it Aborted! 

how do i fix this?

---

### Post by xeth_delta on 2007-12-24
First a short question. Why did you type !/bin/bash? As far as I know, you can use it inside bash scripts, under the form **#!/bin/bash**

About the error. Try issuing an **apt-get -f install**.

---

### Post by hilariousness16 on 2007-12-24
i thanked you lol..:lolflag:

ok back on subject,
i was trying to install this

[http://ubuntuforums.org/showthread.php?p=3594426#post3594426](http://ubuntuforums.org/showthread.php?p=3594426#post3594426)

---

### Post by p_quarles on 2007-12-24
Hmm. That's kinda strange. My only guess: it looks like you have a number of uninstalled updates. Try running this:
```
sudo apt-get update && sudo apt-get upgrade
```
And then run the command for installing those packages again.

---

### Post by xeth_delta on 2007-12-24
Ok, try again

```
sudo apt-get install compiz-bcop compiz-dev
```

If that does not work, try

```
sudo apt-get -f install
```

---

### Post by hilariousness16 on 2007-12-24
Eh...still aborts after i type in "y":mad:

---

### Post by hilariousness16 on 2007-12-24
Ugh i give up, can someone just give me a link to compiz plug in's like 3d window, and fish swimming inside the cube:guitar:

---

### Post by xeth_delta on 2007-12-24
Can you please try using aptitude instead of apt-get? Should look like:

```
sudo aptitude install compiz-bcop compiz-dev
```
If it does not work, post the last lines from the output of
```
cat /var/log/aptitude
```

---

### Post by xeth_delta on 2007-12-24
> **hilariousness16 said:**
> Ugh i give up, can someone just give me a link to compiz plug in's like 3d window, and fish swimming inside the cube:guitar:

I'm afraid I am not of very much use in that subject. I am on Feisty still using Beryl. Hopefully someone else will come soon with some links to that.

---

### Post by p_quarles on 2007-12-24
You can always get independent .deb files from packages.ubuntu.com :
[http://packages.ubuntu.com/gutsy/x11/compiz-bcop](http://packages.ubuntu.com/gutsy/x11/compiz-bcop)

---

### Post by xeth_delta on 2007-12-24
> **p_quarles said:**
> You can always get independent .deb files from packages.ubuntu.com :
[http://packages.ubuntu.com/gutsy/x11/compiz-bcop](http://packages.ubuntu.com/gutsy/x11/compiz-bcop)

p_quarles is right. You can then insall those packages with

```
sudo dpkg -i package_name.deb
```

---

