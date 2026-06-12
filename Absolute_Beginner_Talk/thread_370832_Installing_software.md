---
title: "Installing software"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-26
I am using sudo aptitude update
                sudo aptitude install
When the above has completed it's work; it states that the package I am trying to install 
can not be found.  The package is on my desktop.
Do I need to copy the package to say ' root ' . If so,
how do I do this ?   I have looked at the Linux copy command
but I do not how to use it - but am I on the right track ?

---

### Post by truck87bp on 2007-02-26
if you habe your Ubuntu installed, use the synaptic page manager to add software or add/remove programs

---

### Post by halitech on 2007-02-26
if you have downloaded the install file to your desktop then you won't use apt to install it. Apt is only for packages that are in the repos and get downloaded as you want them.

what is the program and maybe we can find you some install instructions

---

### Post by joshkidd on 2007-02-26
The command:

```
sudo apt-get install XXXXX
```

Where XXXXX is the package that you want to install.  This command installs packages from online repositories.  If you want to install a package from your local hard drive use:

```
sudo dpkg -i package.deb
```

Where package.deb is the name of the package.

---

### Post by ColinP on 2007-02-26
The package is a Webcopier ' httrack_3.40.4-3.1_i386deb '
I have used gdebi but there is a dependency  ' libc6 ' : this is installed according to Synaptic P.M.  So, in desperation, I used all methods advised on the forum but, alas, with no result. I obviously do not know enough about Ubuntu to solve the problem.

---

### Post by Maestro23 on 2007-02-26
> **ColinP said:**
> The package is a Webcopier ' httrack_3.40.4-3.1_i386deb '
I have used gdebi but there is a dependency  ' libc6 ' : this is installed according to Synaptic P.M.  So, in desperation, I used all methods advised on the forum but, alas, with no result. I obviously do not know enough about Ubuntu to solve the problem.

Open a terminal and type(after getting in the directory you download the file to):

> sudo dpkg -i package name

*package name is where your file goes.

Installing in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Good luck.

---

### Post by bodhi.zazen on 2007-02-26
LOL

See here : [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/) 

To install your package,

Open a terminal, go to the location of your .deb (? desktop ?)

Then enter :

```
dpkg -i httrack_3.40.4-3.1_i386deb
```

FYI httrack is in the repositories.

To enable repositories : [http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

