---
title: "Cant Install Automatrix2"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by veagles on 2007-05-18
I get the following error when i try to install Automatrix2:

vik@vik-desktop:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: python2.4 but it is not installable
E: Broken packages


How do i fix this?

---

### Post by chemtut on 2007-05-19
go to the Automatix webpage---they have a forum--you will get help there

---

### Post by aysiu on 2007-05-19
I'd say [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources) then try again.

What do you think you need Automatix for? It may be easier to just install what you think you need Automatix for than to install Automatix itself.

---

### Post by mrbungle on 2007-05-19
i think it's easier using the add/remove from the app menu.   i've run in to problems installing via automatrix also.

---

### Post by Sef on 2007-05-19
> i think it's easier using the add/remove from the app menu. i've run in to problems installing via automatrix also.

That can only be done with Feisty.   Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") for installing from Add/Remove.

---

