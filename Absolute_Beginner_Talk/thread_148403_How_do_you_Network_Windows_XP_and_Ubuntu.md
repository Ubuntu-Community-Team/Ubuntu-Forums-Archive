---
title: "How do you Network Windows XP and Ubuntu"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-22
I have never networked before, so my knowledge is limited. I have tried to learn about netwoking on the internet but progress has been slow. Also I have only had Ubuntu for a few weeks, so my understanding of Linux is limited as well. I still need to connect it to the internet with the Ubuntu machine but I also need my Windows XP machine connected. So I was hoping for an easy solution to networking the two computers together and being able to access internet from both simultaniusly.

Some things about the computers:
Conect to internet over a DSL modem
Linux machine has 2 PCI Ethernet cards
Windows XP has 1 onboard Ethernet card

I can put one or both Ethernet cards from the Linux Machine into the windows one.
I have used Add Applications to add everething I thought was network related.

Thanx in advance for your patiance.

Signed:
Total Network Newb****

---

### Post by belikralj on 2006-03-22
Any help is apprechiated.

---

### Post by KansasJoe on 2006-03-22
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

---

### Post by Brunellus on 2006-03-22
simple solution:

go down to the store and buy yourself a cheap 4-port router/switch.  plug the router into your internet connection (I'm guessing a cable modem/DSL modem?).  Plug your computers into the router.

Voila.  A shared internet connection.

as far as networking the two hosts together to share files/printers:  I believe someone linked you a howto on Samba.

---

### Post by OffHand on 2006-03-22
If you don't have a router like me and use your linux as a gateway you can use this guide: 
[http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing)
That worked for me. You will have to enable root first with "sudo passwd root" (without quotes). Type your normal password and type the password for your root twice. To use root type: su
(Try to use sudo when possible though. Root access can be dangerous if you don't know what you are doing.)

---

