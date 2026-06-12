---
title: "Problems with installing RPM [Resolved]"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by cursebg on 2007-04-07
it keeps showin g me that i don't have the permision to open it. i'm root and i've installed all the dependencies, i think.

here's a link to it , if someone could tell me where's the problem

[http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-5ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-5ubuntu2.1_i386.deb)

edit: i'm using 6.06 LTS and the processor's architecture is x86

---

### Post by yabbadabbadont on 2007-04-07
How come you aren't just running
```
sudo apt-get install rpm
```

Enquiring minds want to know.  ;)

---

### Post by cursebg on 2007-04-07
ok i found that a licence bug has been reported ( [https://bugs.launchpad.net/ubuntu/+source/rpm/+bug/45994](https://bugs.launchpad.net/ubuntu/+source/rpm/+bug/45994) ) . does someone confirm it?

---

### Post by aysiu on 2007-04-07
Why don't you post the *exact* error message you get after you paste these commands into the terminal? ```
sudo apt-get update
sudo apt-get install rpm
```

---

### Post by cursebg on 2007-04-07
because i need this package and some other to obtain my internet access ;) i download and chat here from windows

i'll need some time to do this if there are no other suggestions

ok coming in a few minutes

---

### Post by Maestro23 on 2007-04-07
Be advised guys, he has no internet access on the Ubuntu side.  He is downloading packages from ubuntu packages, copying to flash drive, etc....

---

### Post by cursebg on 2007-04-07
> **Maestro23 said:**
> Be advised guys, he has no internet access on the Ubuntu side.  He is downloading packages from ubuntu packages, copying to flash drive, etc....



yeah, that's right :D, have i forgotten to say it?
here's the stuff it shows me

```
vicho@vicho:~$ sudo apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Errhttp://pt.archive.ubuntu.com dapper Release.gpg
  Could not connect to pt.archive.ubuntu.com:80 (193.136.239.4), connection timed out
50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]
50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]
50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]

50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]





50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]




50% [Connecting to pt.archive.ubuntu.com (193.136.239.4)]
vicho@vicho:~$ sudo apt-get install /home/vicho/Desktop/1/rpm_4.4.1-5ubuntu2.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package



```


if i've understood the above correctly it says that the file is missing, but actually i dragged and dropped it. any ideas?


hey guys i'll try it again, brb

---

### Post by jerryrw on 2007-04-07
ok, your prompt tells me that you are not actually root. $ = user # = root

you will most likely need to run:

sudo dpkg -i your.debian.package.name.here.deb

---

### Post by Maestro23 on 2007-04-07
> **jerryrw said:**
> ok, your prompt tells me that you are not actually root. $ = user # = root

you will most likely need to run:

sudo dpkg -i your.debian.package.name.here.deb

Just to tack on to jerry's post:  [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by cursebg on 2007-04-07
hey dudes it seems that the file was corrupted! i downloaded it again and it worked! thanks anyway , you were great

edit: stay tuned for my next n00by prob :D

---

### Post by Maestro23 on 2007-04-07
> **cursebg said:**
> hey dudes it seems that the file was corrupted! i downloaded it again and it worked! thanks anyway , you were great

Good deal man.  Can you go back to your first post, advanced edit, and mark RESOLVED.

---

