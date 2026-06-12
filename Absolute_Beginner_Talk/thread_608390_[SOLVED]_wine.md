---
title: "[SOLVED] wine"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-11-09
hi can i get a step by step on how to load wine there website is quite confusing i am using ubuntu 7.4

---

### Post by houstonbofh on 2007-11-10
Bring up a terminal windows.  Applications --> Accessories --> Terminal  Now type in the following.
```
sudo ls
```
This is just to activate sudo for the next piped command.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
This adds the WinHQ key.
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```
This adds the Wine repo.
```
sudo apt-get update
```
This updates the list.
```
sudo apt-get install wine
```
This does just what you think it does.
```
winecfg
```
This sets up Wine.

---

### Post by bithkits on 2007-11-10
I found the explanation on the website quite helpful actually :confused:

---

### Post by crazysexycool on 2007-11-10
no valid OpenPGP data found.

thats i error i get when copying and pasting 

cheeseboi@cheeseboi-laptop:/home$ cd ..
cheeseboi@cheeseboi-laptop:/$ ls
bin    dev   initrd          justin      media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib         mnt    root  sys  var
cdrom  home  initrd.img.old  lost+found  opt    sbin  tmp  vmlinuz
cheeseboi@cheeseboi-laptop:/$ sudo ls
bin    dev   initrd          justin      media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib         mnt    root  sys  var
cdrom  home  initrd.img.old  lost+found  opt    sbin  tmp  vmlinuz
cheeseboi@cheeseboi-laptop:/$ sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
cheeseboi@cheeseboi-laptop:/$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
cheeseboi@cheeseboi-laptop:/$ cd ..
cheeseboi@cheeseboi-laptop:/$ ls
bin    dev   initrd          justin      media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib         mnt    root  sys  var
cdrom  home  initrd.img.old  lost+found  opt    sbin  tmp  vmlinuz
cheeseboi@cheeseboi-laptop:/$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
cheeseboi@cheeseboi-laptop:/$

---

### Post by ozylog on 2007-11-10
use synaptic package manager........search wine and apply...

---

### Post by crazysexycool on 2007-11-10
thanks guys wine is working few kinks to work out but its here thanks

---

### Post by Cinne on 2007-12-22
I'm having the same no valid OpenPGP data found problem though my error message simply says:

gpg: no valid OpenPGP data found.

I did try going into synaptic package manager and search for wine but it found nothing.  I have downloaded wine and it is in my home folder, both packed and unpacked.  I even tried going to

[http://wine.budgetdedicated.com/apt/387EE263.gpg]("http://wine.budgetdedicated.com/apt/387EE263.gpg")

Saving the file as wine.gpg and in the terminal typing

```
sudo apt-key add wine.gpg

```
It says OK but I'm still getting the no valid OpenPGP message.  Is there a step somewhere that I missed or am I just doing something wrong?

---

