---
title: "Verizn USB720"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by mpmascorro on 2007-07-10
I am very new to Linux and would love it very much if I could get rid of anything on my computers with M$ name on it.
My problem is I don't know if Ubuntu or any other Linux distro will support my Verizon USB720 wireless modem.
Does anyone know if there is one out there

HELP

---

### Post by darf681 on 2007-08-17
yes it will.  I use kubuntu and use kppp to run it.  mine shows up on /dev/ttyusb0 when i plug it in.  Should be able to set it up using the following info:

Login ID:  [phonenumberwithnodashes]@vzw3g.com
no password

the phone number is #777

you will have to set up your modem in kppp as well as the connection.

cheers!

---

### Post by owlhoot on 2008-06-20
I managed to get mine working, but had to activate the card in windows. I borrowed a friends computer to activate the card. It worked fine after that. I use Gnome PPP to connect, and have excellent speeds. I did double check to be sure that it would work. It recognized the card just fine, and even tried to dial the connection, but as the card had not yet been activated, the account would not work.  If you know some way to activate the card without going through windows, please share it. Otherwise, you need a friend or another computer with windows on it to seal the deal, so to speak.

---

### Post by Jaxl on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=838891](http://ubuntuforums.org/showthread.php?t=838891)

:D works perfect on ubuntu gnome 8.04 GPPP GNOME PPP

$ sudo apt-get install gnome-ppp

---

