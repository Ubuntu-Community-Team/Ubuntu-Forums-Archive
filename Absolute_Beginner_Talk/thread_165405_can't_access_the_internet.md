---
title: "can't access the internet?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by cptmichael101st on 2006-04-24
I've recently moved back home from college, and am now using SBC Yahoo! DSL.  I had no problem connecting to the internet, surfing the web, etc at college going through their proxy, but here at home, there's no proxy and I use a router.

  I can type my router's IP into Firefox and it works fine, and I can ping any other computers on my network without any problem, either.  Yet for some reason, typing "www.google.com" or "www.yahoo.com" brings up the error message "Unable to locate server" (pop-up alert box with OK button) or something to that effect.

  That seems to tell me that the problem is with Firefox's settings.  I've tried setting the connection to both "Direct connection to the Internet" and "Autodetect proxy settings" and both give me the same message.  Is there another setting I need to change, or is the problem elsewhere?

---

### Post by cgjones on 2006-04-24
Are you using DHCP or static IP addresses?

---

### Post by dermotti on 2006-04-24
Maybe you are not picking up DNS properly.

put **[http://64.233.167.99/](http://64.233.167.99/) ** in your browser and see what happens

---

### Post by cptmichael101st on 2006-04-25
Typing in the IP works.  Google was displayed in all its multicolored brilliance.  I verified from another PC on the same LAN that I'm using the right DNS server.  I assume there's something else I need to fix then?

Edit:  I'm using DHCP.

---

### Post by cptmichael101st on 2006-04-26
bump.

---

### Post by gguy on 2006-04-26
my symptoms are almost identical. Tried other settings too. I'm on now using a knoppix live cd so I know this computer can get on.

---

### Post by slivesay on 2006-04-26
you have connection to you're network and are able to connect to google with the ip, its definitly something with dns setup on your computer. 

Check in System > Preferences > Network Proxy that you have connect directly to the internet selected

If it still doesn't work...
From terminal run 'cat /etc/resolve.conf' to ensure that you have the correct nameservers. 
looks like this..
search mydomain.com
nameserver 172.29.1.234
nameserver 172.29.1.236
nameserver 10.0.8.27
nameserver 10.0.8.28

If the correct name servers are in there...

run 'nslookup google.com'
you should get something similar to this

Server:         172.29.1.234
Address:        172.29.1.234#53

Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.187.99

---

### Post by cptmichael101st on 2006-04-27
Well everything seemed to work OK until the nslookup.

I did resolv.conf and got the following:

     search company.com
     nameserver 192.168.1.1

Then I ran "nslookup google.com" and got the following:

     ;; reply from unexpected source: 68.94.156.1#53, expected 192.168.1.1#53
     ;; reply from unexpected source: 68.94.156.1#53, expected 192.168.1.1#53
     ;; reply from unexpected source: 68.94.156.1#53, expected 192.168.1.1#53
     ;; connection timed out; no servers could be reached



Thoughts?

---

### Post by Sef on 2006-04-27
This thread might help you.

[http://www.ubuntuforums.org/showthread.php?p=951507#post951507]("http://www.ubuntuforums.org/showthread.php?p=951507#post951507")

---

### Post by cptmichael101st on 2006-04-27
Alright kids.  I figured out my problem.  Turns out my DNS server was totally different than what I was typing in.  The one I used was from an ipconfig in WinXP, which was totally and flagrantly WRONG!

I double-checked my router settings (typed in the router's IP into Firefox), and sure enough - the DNS was different.

I'm just glad I posted this in the Newbie forums.  Cuz it was definitely a newbie problem!  :-)

Thanks for all the help.

---

