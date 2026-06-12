---
title: "trouble with beginning config"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by LOLercaust on 2006-09-23
im running ubuntu finished the first part of the installation now im in the conifg section.

i used OEM to log in went through that part.

i Added a new user and filled out the info then hit used the EXIT command to reboot.

after the reboot i logged in with the new user i created.

Now its just a blank prompt

Matthew@ubuntu 

what do i do now...?

---

### Post by xXx 0wn3d xXx on 2006-09-23
> **LOLercaust said:**
> im running ubuntu finished the first part of the installation now im in the conifg section.

i used OEM to log in went through that part.

i Added a new user and filled out the info then hit used the EXIT command to reboot.

after the reboot i logged in with the new user i created.

Now its just a blank prompt

Matthew@ubuntu 

what do i do now...?

Did you install a server ? Or just the base system ?

run sudo apt-get install gnome for the gnome desktop enviroment
and sudo apt-get install kubuntu-desktop for kde.

---

### Post by petri on 2006-09-23
Or simply try first with ```
startx
``` at terminal. Did you say you installed an OEM-version of Ubuntu? It sounds like your version is 5.10 called Breezy Badger and not todays version 6.06 Dapper Drake. I believe there is no OEM installation (easily) with Dapper CD.

But if you install a desktop via terminal do please use **aptitude** instead of **apt-get** like this ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` You can find it at [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome) . Browse that site and you will find a lot and easy information about using Ubuntu and reason why use aptitude instead of apt-get.

---

### Post by bulldog on 2006-09-23
> **petri said:**
> Or simply try first with ```
startx
``` at terminal. Did you say you installed an OEM-version of Ubuntu? It sounds like your version is 5.10 called Breezy Badger and not todays version 6.06 Dapper Drake. I believe there is no OEM installation (easily) with Dapper CD.

But if you install a desktop via terminal do please use **aptitude** instead of **apt-get** like this ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` You can find it at [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome) . Browse that site and you will find a lot and easy information about using Ubuntu and reason why use aptitude instead of apt-get.


Yes there is,it's called 'alternate cd'

---

