---
title: "help installin wifi radar"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by magugs365 on 2005-10-21
alright I'm a n00b and I need help  installing wifi radar in 5.10 it says to put the files in /usr/sbin but I dont know how to accss /usr/sbin/ to do this Ive opened the terminal and put that in but it just says that it is a directory any help?

---

### Post by Lambert on 2005-10-21
Welcome to ubuntu/linux. You're going to want to spend some time reading the wiki, top of the forums is a link to the official wiki. ubuntuguide.org is also a good place to spend sometime reading. Not sure if it's updated yet for breezy yet.

google is your friend also.

Go here to learn about installing apps in ubuntu

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications)

---

### Post by magugs365 on 2005-10-21
All I need to know is how to open /usr/sbin/ ( I'm new to Ubuntu I come from slackware)

---

### Post by Lambert on 2005-10-21
to change to that directory type 

```
cd /usr/sbin
```

If you're trying to copy files from one location to another use

```
sudo cp /unzipped_location /usr/sbin/new_directory
```

to install wifi radar you can use synaptic to download from the repositories and it will automatically install all files in their correct location.

Never used slackware so I'm not sure how it differes from a debian based distro.

---

### Post by magugs365 on 2005-10-21
thanks I'll go try that now
slackware is a lot more based on the shell prompt than ubuntu and the installation is longer than ubuntu's

---

### Post by magugs365 on 2005-10-21
im gettin permission denied and im using the root shell

---

### Post by magugs365 on 2005-10-22
Is there a default wifi finder that I can use that comes with Ubuntu 5.20

---

### Post by kingsidy on 2005-10-22
there is an easy way to do just that. First intall wifi radar from the add application in the main menu, go to internet and select wifi radar. after it installs, it will be in the menu: applications>internet>wifiradar. It is going to ask you for you root password, once u input it, the program opens.

---

### Post by magugs365 on 2005-10-22
the only thing is my computer only has the wireless NIC and the the router is on a seperate computer, and you need to go online to install like that

---

### Post by landotter on 2005-10-22
grab this .deb: [http://master.grad.hr/~ivoks/ubuntu/wifi-radar_1.9.4-0ubuntu6_all.deb]("http://master.grad.hr/%7Eivoks/ubuntu/wifi-radar_1.9.4-0ubuntu6_all.deb")

assuming you d/led to the Desktop:
open a terminal:

$ cd Desktop
$ sudo dpkg -i wifi-radar*
$ **** (password)

alt+f2, "sudo wifi-radar".

I've only played with it a little and couldn't get it to run as a normal user.

I've found network-manager and nm-applet to be superior for the average user. You can find it in Synaptic. nm-applet will be installed if kyou install network-manager--something I found confusing. :p

---

### Post by magugs365 on 2005-10-22
how do I login as a user with complete control?Even when I use the root terminal I still get permision denied to copy certain programs

---

### Post by landotter on 2005-10-22
[quote=magugs365]how do I login as a user with complete control?[/quote]

You can't with Ubuntu.

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

