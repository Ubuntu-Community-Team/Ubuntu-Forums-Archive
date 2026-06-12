---
title: "Create network connection between Feisty and Vista for sharing internet??"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-07-16
Hi just looking for a point in the right direction as to what steps I need to take to create a network connection between my Feisty box and my new notebook running windows vista. The only function of this network will be for sharing internet access once its been through the firewall on my Feisty box. Basically my desktop running Feisty will be acting as a firewall between the internet and my notebook. I would be happy just to run an ethernet cable between the two. Anyway just looking for some advice on what I need to get and look at? I am completley new to networking Thanks : )

---

### Post by xpod on 2007-07-16
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Thats how i do it wihtout a router although you need a second nic in the desktop machine as well as a crossover cable for that method.
I can attatch the hub we have to the second nic and connect as many pc`s(7) as i like but i`ll be buying a proper router myself soon i think.

Theres only so much wiring i can hide:)

---

### Post by guilly on 2007-07-16
I run an ftp server under Linux(Ubuntu) but the rest of network is Windows, I had to install SAMBA to be able to share files and see the linux box in my workgroup. Just out of curiousity, why do you want your Linux box to act as a Firewall, would it not be easier to just have seperate firewalls on each? Never the less, if you would like to do this all i can say is that you will defenetly need Two NIC's or the only other option i can think of is going the AD route.

if someone can back up my opinion plz do so.... I'm quite familiar with Windows AD but know NOTHING about where to start with Linux AD

---

### Post by nite owl on 2007-07-17
Thanks for your replies. So I will need Samba for the interface? Im thinking my setup will be: usb modem -> linux box(with firestarter) -> router -> notebook(vista). I am not sure If it would be better with a router or not, However the reason I am using the router in between the two machines instead of after the modem is because I have been told that because my modem has no ethernet interface only usb that It cannot be attached to a router

---

