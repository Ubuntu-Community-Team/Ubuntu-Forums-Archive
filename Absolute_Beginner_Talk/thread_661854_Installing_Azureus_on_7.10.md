---
title: "Installing Azureus on 7.10"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-08
I am trying to install Azureus on Ubuntu 7.10.  I have moved the azureus directory to /usr/lib/azureus.  When I try to install I get the following ouput:

> Starting Azureus...
Java is GCJ.. looking for Sun Java..
Java exec not found in PATH, starting auto-search...
ls: /usr/java/latest: No such file or directory
ls: /usr/java: No such file or directory
ls: /usr/lib/jvm/latest: No such file or directory
ls: /usr/lib/jvm: No such file or directory
Re-checking with GCJ (Sun Java recommended)..
Suitable java version found  [java = 1.5.0]
Configuring environment...
Java exec found in PATH. Verifying...
find: /home/john/.azureus: No such file or directory
ls
Passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]


Any help with this would be appreciated.

Thanks,
jhvillegas2

---

### Post by Perfect Storm on 2008-01-08
You need to install java sun 1.5 or 1.6 to make it work.

I can recommend Deluge for torrent: [http://deluge-torrent.org/](http://deluge-torrent.org/) way better than Azureus

---

### Post by tigerplug on 2008-01-08
Hi jhvillegas2 , 

Im no genius but I think the problem could be with Java  or lack of.

Try this:

```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

After running the installation try:

```
sudo apt-get install azureus
```

Any luck? :)

---

### Post by tigerplug on 2008-01-08
> **Artificial Intelligence said:**
> You need to install java sun 1.5 or 1.6 to make it work.

I can recommend Deluge for torrent: [http://deluge-torrent.org/](http://deluge-torrent.org/) way better than Azureus



Think I might just check that out myself! 

Looks interesting!

---

### Post by Perfect Storm on 2008-01-08
Aye and they have Up to date Ubuntu packages.

---

### Post by tigerplug on 2008-01-08
> **Artificial Intelligence said:**
> Aye and they have Up to date Ubuntu packages.

Gonna download that as soon as I get home.

---

### Post by jhvillegas2 on 2008-01-08
I downloaded Deluge and clicked on the package to install it.  Got an error message reading:

Error:  Dependency is not satisfiable:  libboost-date-time1.34.1.

How can this be resolved.

Thanks,
jhvillegas2

---

### Post by Perfect Storm on 2008-01-08
System ---> Administration ---> software sources

Enable main, universe, restricted and multiverse.
Also you can enable Third-party-software.

The lib you're looking for is in the universe and it looks like your sourcelist havn't been setup.

---

### Post by jhvillegas2 on 2008-01-08
Success with installation of Azureus.  However, I don't know what listen port to set it to.  How do I determine which one is best?  Do you have any suggestions?  I am not running Firestarter.  Thank you much.

jhvillegas2

---

### Post by Perfect Storm on 2008-01-08
The usually ports for this is 6881-6889

---

### Post by jhvillegas2 on 2008-01-08
Now, Azureus immediately closes when I run it. Why does it do this?

---

### Post by Perfect Storm on 2008-01-08
run it via the terminal, the output will tell.

---

### Post by jhvillegas2 on 2008-01-08
what am i supposed to be looking for.......there was a lot of cryptic info, and then the core dumped.

---

### Post by Perfect Storm on 2008-01-09
just post it here.

---

