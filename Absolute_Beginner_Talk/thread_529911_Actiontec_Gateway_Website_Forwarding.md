---
title: "Actiontec Gateway Website Forwarding"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-08-19
So I have an Actiontec DSL Gateway Modem from Qwest. I'm trying to set it up so that when I type in the external IP address, it'll pull up my website on my Ubuntu Web Server. However, everytime I type in the IP address, it comes up with the settings page for my DSL Gateway (it also comes up when I type in the local IP for the Gateway "192.168.0.1"). I thought that all I had to do was forward port 80 to the local server ip (192.168.0.150). It doesn't seem to be working.

Here is a site with screen shots of the Advanced Settings of the Gateway I have: [http://www.coinfotech.com/support/actiontec_advanced_setup_static_ip.htm]("http://www.coinfotech.com/support/actiontec_advanced_setup_static_ip.htm").

I want the website and eventually ftp to be directed to the Ubuntu server. What settings should I change?

---

### Post by curuxz on 2007-09-14
you will need to change the default port for your admin page on the device, which almost certainly is using port 80 already, hence why you keep getting to it.

---

### Post by splintercellguy on 2007-09-14
The problem is that you are using your private IP address to connect. Use a website like [http://whatismyipaddress.com/](http://whatismyipaddress.com/) to determine your public address.

---

