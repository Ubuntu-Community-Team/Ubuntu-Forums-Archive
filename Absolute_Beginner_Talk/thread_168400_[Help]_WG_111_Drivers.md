---
title: "[Help] WG 111 Drivers"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by bugme on 2006-04-30
Hello,
I was just wondering if I could get my wireless adapter the WG 111 (version 1)
to work via the driver files on the windows partition on my computer.
Basically, the wireless adapter is installed with the drivers and everything on the windows partition of my hard drive. How would I get the .inf driver file from the windows partition onto the ubuntu partition?

Also, how do I login as root? What is the default password because I couldn't figure out how to change it?

Thanks in advance!

---

### Post by BlvdKing on 2006-04-30
I am interested in this as well.

---

### Post by zad on 2006-04-30
you could possibly get the drivers you need from linuxant (google that one) you might also need to use ndiswrapper if you use the search on here there is good help already around :)
Easy way to get root is go to the system settings and in the users bit go to root and add a password.then in a terminal type su then password when asked :)

---

### Post by pshnfry on 2006-05-01
Firstly, search the wiki (see link at top of page) re root.  Basically disabled in Ubunto, prefix commands in terminal with sudo and password is your user password.  Once this unique aspect of Ubuntu is known it works quite well.  The how to's also run through how to access root but don't recommend.

Re wifi cards, try this link to a search of the wiki.
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles)

---

### Post by pshnfry on 2006-05-01
[QUOTE=pshnfry]Firstly, search the wiki (see link at top of page) re root.  Basically disabled in Ubunto, prefix commands in terminal with sudo and password is your user password.  Once this unique aspect of Ubuntu is known it works quite well.  The how to's also run through how to access root but don't recommend.

Re wifi cards, try this link to a search of the wiki.
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles)[/QUOTE]

Also, see common threads at base of this page.

---

### Post by sailor2001 on 2006-05-02
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)  find your chipset here and download.........after downloading it to >where ever<  in terminal: 
cd >where ever<    remember ubuntu is case sensitive
sudo apt-get install ndiswrapper-utils
password:
sudo ndiswrapper -i NET8180.INF
sudo ndiswrapper -l
sudo dhclient

once that's done.click ctrl+0 to save
next time you boot-up may need to terminal "sudo dhclient"

---

