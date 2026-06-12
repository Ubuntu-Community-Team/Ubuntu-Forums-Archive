---
title: "Installing Plugins Problem....."
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by sumitsen on 2006-07-10
Hi Friends,

Whenever I try to install some plugin from firefox, or azareus etc. I get an error saying that I dont have the privilidge to write to that plugins folder.

In the command line I can do sudo and get the root privilidges, but how to do it in applications like azereus etc...

Can someone help me please????

Thanks & Regards
Sumit Sen

---

### Post by T700 on 2006-07-10
To start a graphical application in Gnome with root rights:

```
gksudo yourapplicationhere
```

in KDE:

```
kdesu yourapplicationhere
```

for non graphical applications, just use "sudo" instead of "gksudo" or "kdesu".

You might also check out the link for Automatix in my sig.  It will install most common plugins for you, as well as lots of other things to make life with Ubuntu easier.  You can of course, control what it installs.

Paul

---

### Post by rdd on 2006-07-10
That does sound strange. You should have write permissions in your home folder (where your plugin-directory would be too). To make sure you could go to your home directory and press Ctrl-H (Or do it via the View menu) to show the hidden files. Then look for your .mozilla folder (for Firefox and) check the permissions in there. 

rdd

---

### Post by Rackerz on 2006-07-10
To be able to actually install plugins for Firefox I think you NEED to use sudo. For Azureus to update and install the update you need to run 'gksudo azureus' if your running Gnome.

---

### Post by sumitsen on 2006-07-11
gksudo azureus won't even launch azureus.

I can only launch it from the start menu....

I am running gnome. (Ubuntu 6.06)

It is also trying to write some files on the / filesystem and not on the home folder...

---

### Post by T700 on 2006-07-11
> **sumitsen said:**
> It is also trying to write some files on the / filesystem and not on the home folder...

That's the key.  You must have root rights to do that. 

Paul

---

