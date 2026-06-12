---
title: "Network not working"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by e2k on 2006-07-01
I recently installed Xubuntu on my laptop, tried it out with the "live cd" and everything worked fine including my network.. But despite a successful install I can't manage to connect to the internet (ADSL). :o I've got little knowledge on what to look for since I've had a rather long brake from linux, I tried sudo /etc/init.d/networking restart but without any luck.. What should I do?

---

### Post by sinack on 2006-07-01
try this...

run 
sudo dhclient eth0

*I'm assuming that eth0 is your network interface.*

If that works for you, you may want to add a startup script to automatically do that for you.

---

### Post by arochester on 2006-07-01
Have you tried "How to configure broadband connections" at [http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_broadband_connections](http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_broadband_connections)

Basically type:

> sudo pppoeconf

---

### Post by e2k on 2006-07-02
Thanks for your replies!
It seemed as if my modem was completely dead, I tried various other live cd:s with which I've been using our internet for ages, but they had the same problem as my current xubuntu install, network didn't work.. I began to worry that my modem was broken. But today I tried /etc/init.d/networking restart just for the heck of it, and it spawned to life. I have no idea why it started to work NOW, but I'm glad it did.

Next time it fails (if it does), I'll try your advice arochester.. :)

---

