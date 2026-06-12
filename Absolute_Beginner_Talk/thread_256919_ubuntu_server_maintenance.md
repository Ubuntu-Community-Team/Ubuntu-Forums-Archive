---
title: "ubuntu server maintenance"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by edmicman on 2006-09-13
So I've dove head first into linux with an ubuntu server install.....so far so good!  Online tutorials plus what I've picked up from setting up my knoppmyth box helped me set up openssh, samba shares, and I've even got phpmyadmin working, too.  Woohoo!

My question is, how should I go about maintaining and updating my box now?  Am supposed to schedule something somehow?  Do I just occasionally log in and do "apt-get update"?  Does that even update everything that's on the box?  Thanks for any info or pointing in the right direction!

---

### Post by stmiller on 2006-09-13
Yes I would do regular updates, as it is good for a server box to be secure. Make sure you have iptables running as a firewall, if you need that. (Firestarter? I think is a GUI for iptables)

It's perhaps a good idea to edit the /etc/dhcpd.conf file and add entries for computers on your network. This will give them default ip addresses on your network. Makes it easier for port forwarding, or ssh'ing to a known address.

---

### Post by Kilz on 2006-09-13
The sequence is 
```
sudo apt-get update
```
This updates the list of avaialable packages, then
```
sudo apt-get upgrade
```
To actualy upgrade the system.

---

### Post by edmicman on 2006-09-13
Thanks for all the info!  It's just an internal server on my home network....it's behind a router and all and isn't available from outside the network (at least not yet) so it should be set.  

For the upgrading/updating, should I automate that on some type of schedule?  How does that usually work?

---

### Post by jordanmthomas on 2006-09-13
You could use cron
```
man cron
```
to set up automatic updating.

---

### Post by edmicman on 2006-09-13
Thanks, I'll check that out.

---

### Post by Jingo on 2006-09-23
Again...
Would it be posible to get an email listing the packages available for update ?

I'm thinking of a update-notification aka Ubuntu-desktop's, just email instead of gui!

---

### Post by jordanmthomas on 2006-09-24
```
sudo apt-get update
sudo apt-get upgrade
```
It will ask if you are sure before updating and will tell you what is to be updated.  So, you don't really need an email

---

