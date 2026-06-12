---
title: "Apache from the Web?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-11-24
I posted this in Networking but so far no responses so i figured I'd try here. 
I'm using Apache to work on my web pages & test them before I upload them to my Web Host.
I have Apache loaded on 1 computer & can access its web pages through any of my other computers hooked up to the same router by typing the correct IP address in a web browser or "localhost" on the Apache computer. I want to view the Apache computer web pages from the
internet from anywhere.
Can anyone tell me what I need to do?

---

### Post by andhar on 2007-11-24
if you want to do this permanently and to host your own pages then you will need to make a static ip on the pc with apache running on it. 

Then in the router setup port forward port 80 to the ip of the system running apache.

How to Port forward
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Setup static IP
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

When made the ip on my server static I just right clicked on the wired connection icon and was able to do it from there.  Keep in mind u will need your ISPs DNS settings as well so make sure u have ALL the info b4 you procede so you dont get frustrated.

You may also want to sign up to no-ip as well.
Good luck.

---

### Post by garyed on 2007-11-24
Thanks for the help,

---

