---
title: "RPM File command not recognized"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by aberto2k on 2006-07-15
Hi all, 

I'm new to linux - I'm sure you're all shocked :p  .

I've just installed Ubuntu LAMP server (and the GNOME interface) and I'm having trouble installing the drivers for my Brother 1470N printer - a network printer connected to a router.

I've downloaded the CUPS Driver and the instructions are quite clear -- but when I use the following command:

rpm -ivh --nodeps brhl14_2-1.0.0-0-noarch.rpm

I get : bash: rpm: command not found

Being based on Debian shouldn't there be no issue using rpm? or am I missing a step - like installing something else first?

Any help would be appreciated,

Aberto2k

---

### Post by GuitarHero on 2006-07-15
Debian doesn't use rpm's, it and its derrivitives(ubuntu) use .deb's

---

### Post by 3rdalbum on 2006-07-16
I'll be more helpful. Because RPMs are not the native Ubuntu package format, you must convert them to .debs (which *are*)

Go into the terminal and type:
```
sudo apt-get install alien
```

Now you can use the *alien* program to convert your RPM to a DEB.

```
alien brhl14_2-1.0.0-0-noarch.rpm
```

Now double-click on the Debian package that will appear. You'll then be able to install it, and hopefully then use it.

---

### Post by aysiu on 2006-07-16
You don't need to convert the .rpm to a .deb and then install the .deb. You can do the conversion and installation together with one command: ```
sudo alien -i brhl14_2-1.0.0-0-noarch.rpm
``` As 3rdalbum pointed out, though, you'll need the *alien* package installed first: ```
sudo aptitude update
sudo aptitude install alien
```

---

### Post by aberto2k on 2006-07-16
Thank you all very much, it worked beautifully.

Now on to configuring the webserver. :)


Thanks again,

Aberto2k

---

