---
title: "Server on feisty?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2007-07-15
Hello there I'm using Ubuntu feisty I'd  already installed a LAMP server before,now i want to test if this works via internet.
What is the address which someone types to "view" my files in the var/www folder?
What type of address is required how can i know if my ip is static or dynamic? 
A! do not forget to mention that before the installation of my modem (sagem 840) I used to type 127.0.0.1 to view my files of my "demo" server and everything was ok,now after the installation it doesn't work,what's going on?
Sorry for my bad English
Thanks for your patience.

---

### Post by Jimmyfj on 2007-07-15
To view your IP address go to Programs-->Accessories-->Terminal and open a terminal window. At the terminal you type: ifconfig - and look for an address starting with 192.168.*.* the stars representing the last numbers of your specific IP address. Once you have the correct IP address you type it in a browser this way: [http://192.168.1.100](http://192.168.1.100) (just a sample address) And the Apache web server should respond with a page saying: IT WORKS.

To know if your IP adress is static or dynamic you'll have to contact your ISP, Internet Service Provider, but unless you specifically ordered a static your ISP provides you with a dynamic address most of the time. You do not need a static IP to run a server - You can also use DynDNS - I believe you find them at:

[http://www.dyndns.com](http://www.dyndns.com) or something similar.

Good luck.

Edit: If you have a router on your net facing the Internet you're also able to view the current IP address through there!

---

### Post by chemicalgr on 2007-07-15
Thanks Jimmy

---

