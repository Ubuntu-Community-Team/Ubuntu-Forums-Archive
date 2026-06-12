---
title: "Network Manager install: Dependency problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by wgw on 2007-03-23
I uninstalled networkmanager at one point when I was trying to get my wireless going. (Using Wifi-Radar now instead)

Now I am trying to reinstall it. With Synaptic, I get an error message: 

> 
Could not mark all packages for installation or upgrade

The following packages have unresolved dependencies. .... 

Network manager :  
       Depends: libdbus-1-1 but it is not going to be installed
       Depends: libdbus-glib-1-1 but it is not going to be installed
       Depends: bind9 but it is not going to be installed



libdbus-1-3 and libdbus-glib-1-2 are installed on my machine according to Synaptic, and  I found files in /var that have that name. If I try to mark libdbus-1-1 for install in Synaptic I get a long list of packages that will be removed (ending with Yelp!) and I doubt it is a good idea to proceed with the installation, given all the changes. 

I also wonder if I have confused things by installing from [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) which is marked as a Breezy repository (I am under Edgy 6.11) according to Synaptic.

I'm guessing NetworkManager can use libdbus-1-3 etc.. Is there a way to fix the dependencies? What is the best way to fix this problem. 

(I have tried various sudo apt-get -f install, sudo aptitude upgrade, sudo apt-get autoremove. No luck.)

Thanks in advance for any suggestions.

---

### Post by zvacet on 2007-03-23
Yes you have confused things.delete that packages and be sure that you have all repositories open and source list correct(Edgy only).I use this list
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")
but as you see at the bottom of that page that is not only choice you have.You can have your desired packages if you go to FF search engine and under Ubuntu packages type name of package you want to install.

---

### Post by wgw on 2007-03-24
Thanks very much for the reply: I will give it a try...once I have my system booting again! But that is another (long) story! (The short version: I fiddled a bit too much and through either a get-apt update, upgrade or a autoremove or something, I am now confronted with the terrible /sbin/init not found problem. There is much discussion on the forum about that problem, so I will wade through it using another computer.)

Thanks for the (safe) list of repositories.

---

