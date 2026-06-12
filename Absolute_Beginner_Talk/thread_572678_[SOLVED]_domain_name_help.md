---
title: "[SOLVED] domain name help"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-10-10
i talked to a godaddy representative and he helped me up to the point where i had to configure my server... i have a domain (kviero.com) what do i do server side to make them talk? i have webmin, ubuntu server 7.04, and bind dns (which i can kill if needed) so... help!

---

### Post by kthakore on 2007-10-10
You need to install and configure bind9. 

Try this guide
[URL="http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html"]
http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html[/URL]

---

### Post by milosz.galazka on 2007-10-10
What you want to achieve?

Solution 1
If kviero.com is resolved to ip of your server then you just need to edit */etc/hosts* file by adding kievro.com, set *hostname* and configure web server.

Solution 2
If your server acts as DNS then search for how to about configuring bind nameserver and as usual modify */etc/hosts* file and set *hostname*. Then you could configure apache or other software.

---

### Post by kevin11951 on 2007-10-10
ok, solution 1, how do i do that?

---

### Post by llamakc on 2007-10-10
Log on to your GoDaddy web control panel and set the IP for your hostname to your server.

Tell your router (if you use one) to open port 80 to your internal IP. If you don't use a router and are directly connected, have you installed apache2 yet?

---

### Post by kevin11951 on 2007-10-10
i did all the godaddy stuff, and router stuff, but my site ([www.kviero.com]("kviero.com") as you can see) wont work.

---

### Post by llamakc on 2007-10-10
Is apache2 installed yet?

---

### Post by kevin11951 on 2007-10-10
yes

---

### Post by llamakc on 2007-10-10
Does apache work if you open 127.0.0.1 in your browser?

---

### Post by llamakc on 2007-10-10
nslookup says your external IP is 208.69.32.132 for kviero.com, however I can't get your web server by name or IP either.

Are you certain you have opened the port on your router? One way to troubleshoot is to make your internal IP be the DMZ (if your router has that designation).

Next, are you certain your provider allows traffic over port 80?

---

### Post by llamakc on 2007-10-10
Also, what happens if you type:

sudo apache2ctl fullstatus

---

### Post by kevin11951 on 2007-10-10
im in the middle of reformatting it now, because it died, ill see what it does when it wakes up.

---

### Post by milosz.galazka on 2007-10-10
Log on to godaddy account and assign kviero.com to your ip address. It will take some time before your name will be resolved. But you could access it by name (if you want) by editing */etc/hosts* file on your home computer by adding line
```
ip.address.of.server kviero.com
```

Then log on to your server.
Edit */etc/hostname* file. It should contain your hostname like *kviero.com*
Edit */etc/hosts* file. You will see ip adresses and names so just add kviero.com [www.kviero.com](www.kviero.com) or whatever you need here. Something similar to
```
this.server.ip.address www www.kviero.com kviero.com
```

Disable bind, you could uninstall it later. (command like *update-rc.d bind remove*)

Run ```
/etc/init.d/networking restart
``` or reboot server.

There are somewhere here links about securing ubuntu server and configuring apache/lighttpd/... as web server.

I just need to have couple hours of sleep before going to work ;p so sorry if wrote somewhat chaotically

---

### Post by kevin11951 on 2007-10-10
however before this whole domain thing i used the external ip, and it worked great (but you cant hand out external ip to people)

---

### Post by kevin11951 on 2007-10-10
I Give Up!!!! I Unplugged The Server!

---

### Post by Dr Small on 2007-10-10
If when an External IP address worked in the browser, then all you had to do, is point your domain to the external IP. If not, then ports are closed somewhere along the line.

Dr Small

---

### Post by kevin11951 on 2007-10-11
the problem was the incoststancy... you would type it in, get the page, then click on a link on the page (that worked when going through external ip) and it would just hang, or give you an error page. anyway i gave up.

---

### Post by hyper_ch on 2007-10-11
Do you have a static IP address?

---

### Post by kevin11951 on 2007-10-11
yes, i have an static ip

---

### Post by hyper_ch on 2007-10-11
You could do a ISPConfig install according to [http://www.howtoforge.com](http://www.howtoforge.com) and then follow this tutorial here: [http://www.howtoforge.com/ispconfig_dns_godaddy](http://www.howtoforge.com/ispconfig_dns_godaddy)

---

### Post by kevin11951 on 2007-11-12
nevermind, i figured it out, i just had to revert back to a godaddy dns server (hosting server) and change the @ mx record to my external i.p. 

thanks anyway!

---

