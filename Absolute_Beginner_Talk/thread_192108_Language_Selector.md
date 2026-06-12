---
title: "Language Selector"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-06-08
Hi 
I having a some problems with language selector. When I open the the Language Selector it asks me:
```
Update language support?

Some packages for full language support are not installed on your system. Do you want to install them now?
```
When I click Install Now it says:
```
Warning
The following problems were found on your system:
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

```
Then I click ok and it says:
```
Error:
Could not apply changes!
Fix broken packages first.
```

How can I solve this problem, I have already tried running these:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by learning on 2006-06-08
I'm a newbie but since no-one else has jumped in yet...

Looks to me like you may have a repository problem, so you can't get the packages you need.

Try and get some other program in synaptic and see if you get the same error.

There have been plenty of threads on repositories if you do.

---

### Post by rameez on 2006-06-08
I get the same error when I open synaptic

---

### Post by learning on 2006-06-08
Check this out.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by learning on 2006-06-08
you could also generate a new list using [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

and then replace it from the command line.

Type this in terminal:

sudo gedit /etc/apt/sources.list

then copy/paste the list you generate from the page above.

---

### Post by rameez on 2006-06-08
thanks learning I generated a new list and it fixed the problem

---

### Post by learning on 2006-06-08
Glad it worked for you!

I have to post questions all the time, about time I was able to answer one!

---

