---
title: "Network Manager cannot be installed on i386?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-10
Hello

Just tried to install network manager using the add/remove... function and it says it can't be installed on my computer type (i386).

any help much appreciated as i can't connect to my wireless network at the moment.

---

### Post by mikewhatever on 2007-03-11
What happens if you try > sudo apt-get install network-manager-gnome

---

### Post by pete stahl on 2007-03-15
> **mikewhatever said:**
> What happens if you try

I have the same problem and wanted to try Network Manager to get my wireless card to connect to my network but it isn't installed. I'm also using Dapper. This is the error I got. Can you help, I need detailed instructions on how to do this, still very new to this stuff.

thanks, Pete

> ps@ps-desktop:~$ sudo apt-get install network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package network-manager-gnome
ps@ps-desktop:~$ sudo apt-get install network-manager-gnome
Password:

Sorry, try again.
Password:
Sorry, try again.
Password:

---

### Post by halw on 2007-03-15
Make sure you have the additional repositories enabled.

System > Administration>Synaptic>Settings>Repositories

---

### Post by lamalex on 2007-03-15
... that means your password is wrong. Is there something I'm missing?

EDIT: Disregard that statement, didn't realize they were two different posters. my bad.

---

### Post by pete stahl on 2007-03-15
I found this file network_manager_0.6.2-Oubuntu7_i386.deb and downloaded and transfered it to Ubuntu PC and double clicked on the package and get a error message saying: 
Error: Dependency is not satisfiable: nibln1-pre6

What is wrong or what am I missing??

---

### Post by pete stahl on 2007-03-15
> **halw said:**
> Make sure you have the additional repositories enabled.

System > Administration>Synaptic>Settings>Repositories

How do I do that? I went in and checked the ones that weren't checked and hit reload and it's trying to download the files. I can't get my wireless card to work, that's why I wanted to try Network Manager.

---

### Post by forrestguide on 2007-03-15
> **mikewhatever said:**
> What happens if you try

Hi I just tried it and got this:

nightjar@MSHOME:~$ sudo apt-get install network-manager-gnome
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What does that mean?

Greg

---

### Post by mikewhatever on 2007-03-21
I recently got the error in the topic after having edited my sources list. The package I was trying to install from Add/Remove... could not be found which must have been the reason for the error. In short, extra repositories must be added to the sources list. In 6.10, System>Administration>Software Sources, and make sure Universe and Multiverse are enabled. Then run > sudo aptitude update
sudo aptitude upgrade

A different way is outlined [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by forrestguide on 2007-03-21
> **mikewhatever said:**
> I recently got the error in the topic after having edited my sources list. The package I was trying to install from Add/Remove... could not be found which must have been the reason for the error. In short, extra repositories must be added to the sources list. In 6.10, System>Administration>Software Sources, and make sure Universe and Multiverse are enabled. Then run 

A different way is outlined [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Thank you.  I'll certainly check it out.

Greg

---

### Post by i.am.canadian on 2007-03-21
Hi this may seem like a silly question, but is network manager available for dapper?  That may be your problem, that it is not in the repositories.  This may also explain why the depdnency was not satisfied, namely it doesn't exist on the older system.

However, what you could try doing is getting network-manager form source and compiling it.  You can get the source here [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/]("http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/")  and then follow these basic instructions [http://www.pcworld.com/article/id,127601-c,linux/article.html]("http://www.pcworld.com/article/id,127601-c,linux/article.html")

So, that may or may not be of any use to you, but I hope it is enlightening anyway.  Cheers.

---

### Post by undertakingyou on 2007-03-21
Whenever I have installed Network Manager I have used ```
sudo apt-get install network-manager
```Worked for me.

---

