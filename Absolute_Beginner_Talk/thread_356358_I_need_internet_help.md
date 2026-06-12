---
title: "I need internet help"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by DrLilo on 2007-02-08
Ok, I'm really stuck, since installing Ubuntu, my laptop refuses to connect to the internet. I'm with Bulldog and have a wireless router that is configured via a web interface. However, my PC doesn't have a wireless card so I plug it into one of the router's 4 ethernet ports.

This always worked with Windows but has now stopped working... What's more, I actually tried reinstalling XP and found the internet non-functional there too. I'm now back on Ubuntu, and worried as Hell.

 Through the magic of the Nintendo Wii's Internet browser, I have confirmed that there is nothing wrong with my connection or my router (hence being able to type this now).

I've used my Wii to acess the config of my router and tried everything from fiddling with IP addresses to restoring the whole thing to factory settings...

The kick in the teeth is that my router is convinced that my laptop IS connected to the net... What's more Ubuntu's Networking settings are convinced the laptop is connected to the net... Tell that to Firefox.

---

### Post by apjone on 2007-02-08
in a terminal type

```

ipconfig

```

and post results here.

It could be DNS. 
in fire fox goto 64.233.167.99 , this should load up google , if it does then check your routers config and write down the IP address of the DNS server's it use's.
now open a terminal and type 
```

sudo gedit /etc/resolv.conf

```
now insert
nameserver ip of 1st address of DNS Server
nameserver ip of 2nd DNS Server

then save and exit. Now you should be able to goto ubuntuforums.org or where ever you want by name.

else post the results of ipconfig here.

---

### Post by DrLilo on 2007-02-08
Google did not load, it behaved exactly as it does when I simply type [www.google.com](www.google.com), which is to try and connect for a couple of minutes before reporting that "the connection was reset."

I tried typing ipconfig into a terminal but it says "command not found", am I missing something?

---

### Post by apjone on 2007-02-10
its : 
ifconfig 

sorry been working on a Windows box prior to posting

---

