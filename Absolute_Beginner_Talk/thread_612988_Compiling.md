---
title: "Compiling"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by GamesForLinux on 2007-11-14
I'm a new Ubuntu user with no internet access, so installing things is always a pain. However, sometimes I download a .tar archived program that turns out to be just source code. I don't have any idea of how to compile them, and the readme's are always cryptic and unhelpful to a newbie like me. Could someone point me to a HowTo that would show me where to start? Thanks.

---

### Post by taurus on 2007-11-14
If you need to compile or build something from source, you need to install the build-essential package first.  Good news is that it is on the CD.  So, insert the installer CD into a drive, open a terminal, and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by sailor2001 on 2007-11-14
[http://monkeyblog.org/ubuntu/installing/#not_available](http://monkeyblog.org/ubuntu/installing/#not_available)

---

### Post by Shazaam on 2007-11-14
This might help....

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Paul820 on 2007-11-14
To compile programs with linux there is usually a package available in synaptic package manager called build-essential that installs all the tools for building from source. But...you have no internet connection so you can't use that. :( It can be very difficult to use ubuntu without an internet connection. You can have a look at this link and see if you can resolve all the dependencies for each program that you need [http://packages.ubuntu.com/gutsy/source/gcc-4.2]("http://packages.ubuntu.com/gutsy/source/gcc-4.2")
Have a look at g++-4.2 and then get all the dependencies that it requires. Good luck :)

---

### Post by taurus on 2007-11-14
> **Paul820 said:**
> To compile programs with linux there is usually a package available in synaptic package manager called build-essential that installs all the tools for building from source. But...you have no internet connection so you can't use that. :( It can be very difficult to use ubuntu without an internet connection. You can have a look at this link and see if you can resolve all the dependencies for each program that you need [http://packages.ubuntu.com/gutsy/source/gcc-4.2]("http://packages.ubuntu.com/gutsy/source/gcc-4.2")
Have a look at g++-4.2 and then get all the dependencies that it requires. Good luck :)

Package build-essential IS on the installer CD (desktop and alternate).

---

### Post by Paul820 on 2007-11-14
I didn't think it was on there. That's good to know. :) Disregard all i said then,**taurus** has corrected me.

---

### Post by GamesForLinux on 2007-11-26
Thanks for your help. Unfortunately, my installation of Ubuntu doesn't match any of the disks I have lying around, so it wants me to update a dozen things off the internet before I can install build-essential :(

---

