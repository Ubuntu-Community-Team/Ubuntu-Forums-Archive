---
title: "Installing Kstars In Ubuntu"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jte091805 on 2007-06-13
Hey!

I have downloaded kstars-1.2.tar.bz2. How am i going to install this on my Ubuntu 7.04? 

Please give codes and complete instructions. I'm new to linux and ubuntu. Thanks

---

### Post by Anonii on 2007-06-13
Please, read this: [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
it will solve all your questions right away.

PROTIP: You are doing it wrong. Ubuntu has a package manager. Downloading the tarball like you did (the tar.bz2 file) is not the way that Ubuntu installs applications.

---

### Post by Moop on 2007-06-13
You didn't need to download it. You can install Kstars from the add/remove applications menu. :KS

---

### Post by jte091805 on 2007-06-13
I can use apt-get install if i have internet connection. 

I dont have internet connection at home which is why i download files in my office and then install it at my stand alone ubuntu home PC. I need instructions on how to install it without connecting to internet. thanks

---

### Post by bailout on 2007-06-13
you will find it very difficult tbh. I have a poor internet connection and sometimes dl packages from the ubuntu repos to install but this requires an internet connection that at least works well enough to use synaptic/adept to find out the dependencies. The kstars package will rely on other packages being installed (probably lots of kde libraries that you won't have if you run gnome).

This issue of being able to dl packages on a seperate pc to install on one without a connection crops up regularly and I really think ubuntu should set up a web based system to handle it.

---

### Post by Anonii on 2007-06-14
> **jte091805 said:**
> I can use apt-get install if i have internet connection. 

I dont have internet connection at home which is why i download files in my office and then install it at my stand alone ubuntu home PC. I need instructions on how to install it without connecting to internet. thanks
Okie. You can do it that way too. 
Get in this link: [http://packages.ubuntu.com/edgy/science/kstars](http://packages.ubuntu.com/edgy/science/kstars)
and you will see the dependencies of kstars. You will also see the dependencies of dependencies of kstars, etc.
What you have to do now is download what you don't have. Put them in a directory and execute:
**sudo dpkg -i *.deb** from the terminal.

But well, it will be quite hard to have a working (Linux) PC without the internets.

---

