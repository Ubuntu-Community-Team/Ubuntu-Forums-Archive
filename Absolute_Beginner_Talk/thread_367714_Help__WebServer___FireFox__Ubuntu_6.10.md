---
title: "Help / WebServer  / FireFox / Ubuntu 6.10"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gmutt on 2007-02-22
Another dumb newbie question I am sure.

Have Ubuntu 6.10 Installed with no other OS

Firefox Web Server does not seem to operate when logged in.

Get: Unable to Locate Server Error

Only way I can access Internet is through Live CD

Sound familiar to anyone?******

---

### Post by capdog on 2007-02-23
Well, the problem is that your network is not being configured properly. How do you connect to the internet? ADSL, modem, wireless, smoke signals? :)

---

### Post by airtonix on 2007-02-24
the other issue is that you are not using a webserver to access the internet.

firefox is a viewer not a server.

the server error you recited is infact talking about the lack of response from another computer....

if you connect via adsl...or through another computer...

gateway : 10.1.1.1 [or insert ip or computer or adsl modem ]
mask : 255.255.255.0
dns : the ip of your isp dns server


these three things are the minimum requirements for network/internet connectivity

---

