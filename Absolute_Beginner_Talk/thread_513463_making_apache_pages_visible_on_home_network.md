---
title: "making apache pages visible on home network"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-07-30
Hello All

I have a wireless laptop and a Xubuntu desktop hard wired via homeplug adaptors. Both run from a Netgear ADSL modem/router/wifi base station.

Xubuntu runs apache and has a wiki that I can use from localhost on that machine.

How can I arrange things so that typing a web address on the wireless laptop brings up a Web page being served from the web server on Xubuntu? I'd rather the pages were visible inside the firewall that is in the Netgear router. I'm not trying to share files (yet) just use http.

Any suggestions as to how to get started or even what problem it is that I am trying to solve?

---

### Post by rainbowed_man on 2007-07-30
Hi.

From **a terminal** on the wireless laptop, you can type either:
[LIST]
[*]ifconfig if the wireless laptop is on a GNU/Linux flavour such as Ubuntu
[*]ipconfig if the wireless laptop is on Windows
[/LIST]

and in the output, you can look for the laptop's network IP address. If you're confused, pastebin the output using e.g. [http://rafb.net/paste](http://rafb.net/paste) and link us to it.

To open a terminal, you can:
[LIST]
[*]On Windows, Start>Run, type "cmd" in the input box, and press enter.
[*]On a GNU/Linux flavour such as Ubuntu, you can usually go to Applications > Accessories > Terminal. If that fails, simply type ALT+F2, type xterm in the input box, and press enter.
[/LIST]

and then you can use the IP address given by either tool on the desktop to browse to the HTTP server on the laptop. (If I'm understanding you correctly)

---

### Post by compiledkernel on 2007-07-30
Theoretically Apache is already serving pages, just a matter of hitting the right address to get there. 

Are your addresses local? (192.168.x.x, 10.0.x.x, etc) Or are they public (69.15.14.x or something of the such)? 

Assuming you have local addresses assigned to your machines , itd just be a matter of pointing to that address proper [http://whatevertheaddressis/wiki/](http://whatevertheaddressis/wiki/) (assuming your wiki install is in /var/www/wiki ). 

refer here and here 
[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)
[http://doc.gwos.org/index.php/HowToServerGuide#Apache](http://doc.gwos.org/index.php/HowToServerGuide#Apache)

---

### Post by keithpeter on 2007-08-21
Thanks for replies - I've been offline for a few weeks as (believe it or not) a delivery lorry demolished the telephone pole that carries the phone lines to our little development of 5 houses, and, yes, it takes a large multinational in a rich industrial country weeks to repair the damage.

The Web server is on the Ubuntu desktop running apache, and the wireless laptop is an iBook running Mac OS. I'll try some of the ideas here and post back when I'm next in a wifi cafe or when BT get around to fixing the telegraph pole.](*,)

---

