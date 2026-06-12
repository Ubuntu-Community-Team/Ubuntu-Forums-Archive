---
title: "Firefox or Ubuntu Problem?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by the_Reverend on 2007-02-26
I'm really interested in migrating to Unbutu, so I decided to install it on an older P3 computer I had kicking around.

My main desktop computer is used for just about everything, and my laptop is mainly for work.  The Laptop is a web server (strictly intranet) running IIS.

From my desktop machine, I can access any website project I'm working on by opening up my browser and using an address like:

```
http://laptop/project
```

When I tried this in Unbutu, Firefox automatically adds www. and .com to the address so it looks like:

```
http://www.laptop.com/project
```

Which is not what I wanted.

How do I get Firefox to stop adding the extra bits to the address?  And if I can get it to stop, will it resolve the hostname properly?

I'm using a Linksys router to share my ADSL between the 3 computers.

I appreciate any help you guys can provide me.

Thanks!

---

### Post by jimbren on 2007-02-26
I think Ubuntu is not finding the machine named 'laptop.'  I assume you've got a DNS server in there somewhere?  If not, try adding the IP address for laptop to your /etc/hosts file.  That should take care of it.

---

### Post by the_Reverend on 2007-02-26
The router should be acting as the DNS server for the internal host names.  (At least I think thats what its doing for the Windows machines).  It's also set up as a DHCP so it hands out IP addresses dynamically.  

Adding addresses to a hosts file would be pretty useless since the address I had for "laptop" yesterday most likely isn't the same as what it is today.

Is there a file I should maybe check to make sure that the address of the router (192.168.1.1) is included in the DNS lookup?

---

### Post by the_Reverend on 2007-02-26
I've tried adding the router address (192.168.1.1) to both the DNS server list, and the Search Domains list in the Network Settings section (System>Administration>Networking) and nothing seems to work.

Does anyone have any suggestions?

---

### Post by Dr Small on 2007-02-26
find out what IP is assigned to "laptop" and type that IP in Firefox to connect to that computer.  :S

Dr Small

---

### Post by the_Reverend on 2007-02-26
Yes, using the IP address of the laptop does work, but having to look up the laptop's IP address each time it gets booted is a bit of a pain.  Plus Cookies will always be reset each time I have to use a different IP.  If I can use the Hostname, then Cookies will remain consistent and I don't have to burn neurons by remembering to look up IPs. :p

---

### Post by Dr Small on 2007-02-26
I don't understand why the computer would change IP Addresses everytime on reboot, as my desktop constantly is rebooted and never changes IP Address (and I'm using a router.)

The only time my IP gets changed, is during storms, when it cuts the power out and it resets the router :P
So, I just memorize my IP, and all is safe for me.
But, I see your point, as it would be easier to just type in the name of the computer.

I don't know, but you could try doing the same thing with Konqueror or Opera. Maybe you'll have better luck with them :) (although I am not a fan of either of them :P)

Dr Small

---

### Post by RbikeRider on 2007-02-26
You should set your laptop (IIS Server) to a static IP address.  You can leave your other computers set up for DHCP.  Then as jimbren said earlier "I think Ubuntu is not finding the machine named 'laptop.' I assume you've got a DNS server in there somewhere? If not, try adding the IP address for laptop to your /etc/hosts file. That should take care of it."

---

### Post by the_Reverend on 2007-02-27
I was playing around a bit more, Installed Apache, MySQL, and PHP5 on Ubuntu and got everything working properly.

From any windows machine, I could access the Apache default "Apache's been installed properly" page.  I could only access that using the IP address though.  Using the hostname of the Ubuntu machine didn't work.

So, for Ubuntu, hostnames don't get resolved automatically like they do in windows.

This means I probably have something set up incorrectly in Ubuntu. :p

For now, I'll just live with using IP addresses.

Thanks for the help though.  The experience I've gained here has already granted me a new level.  I am now a level 2 Linux user with a keyboard of confusion +1.

;)

---

### Post by Detonate on 2007-02-27
I think you can make firefox stop adding the "www" and "com" by editing the about:config page and look for these two entries.

browser.fixup.alternate.prefix
browser.fixup.alternate.suffix

If it breaks firefox, you can always put them back:)

---

### Post by the_Reverend on 2007-04-14
For those who are interested, my problem was solved by visiting this post:
[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

I had to set up SAMBA to broadcast my network ID, then everything worked as needed.

J.

---

