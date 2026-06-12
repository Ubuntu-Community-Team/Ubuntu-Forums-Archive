---
title: "dns services &amp; gaim"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-19
if i want gaim to connect i have to delete the 192.168.0.1 from dns services. why is that? and why won't it stay deleted?

---

### Post by r4ik on 2007-02-19
If your router is using dhcp:

The best bet would be to put your isp's primary and backup dns server addresses in your router's setup page. That way, when /etc/resolv.conf gets overwritten upon re-lease or reboot by dhclient, your isp's dns addresses will be there. Dhclient sometimes stops detecting anything beyond the dns-forwarder in our low-cost routers - but that is a whole different story - not dhclient's fault!)

The other option is to manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

Manually editing addresses in /etc/resolv.conf when you are running dhcp in the router only lasts temporarily as dhclient will overwrite /etc/resolv.conf upon re-lease or reboot. Making resolv.conf read-only doesn't work, and using chattr to make it immutable isn't advisable.

Of course you could run static and resolv.conf will be left the way you edit it, but what fun is that? 

I also disable IPV6 globally by running the following as root:
Code:
echo "blacklist ipv6" > /etc/modprobe.d/blacklist


Also try about:config in the adresbar and set the "pipe" maxrequest to 8

then followup by disabling ipv6 in Firefox as well. At this point I just reboot...

if it does not "stick" go to Admin Networking DNS and add the adresses there also.

Hope it helps !

Good luck !

---

### Post by lunaz on 2007-03-18
[color=blue]sorry i'm so late coming back to this lol[/color]

> **r4ik said:**
> If your router is using dhcp:

The best bet would be to put your isp's primary and backup dns server addresses in your router's setup page. That way, when /etc/resolv.conf gets overwritten upon re-lease or reboot by dhclient, your isp's dns addresses will be there. Dhclient sometimes stops detecting anything beyond the dns-forwarder in our low-cost routers - but that is a whole different story - not dhclient's fault!)

[color=blue]i did that, and ubuntu still gets the 192.168.0.1 & 1 dns that's correct[/color]

The other option is to manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

[color=blue] i tried to do sudo nano /etc/dhcp3/dhclient.conf & it made a new file...not sure what the original is suppose to look like or how to find it. EDIT! i got this one done. i did gksudo gedit & got the file!! EDIT2: now i see in networking > dns: realaddy1, realladdy2, 192.168.0.1 :(:(:([/color]

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

Manually editing addresses in /etc/resolv.conf when you are running dhcp in the router only lasts temporarily as dhclient will overwrite /etc/resolv.conf upon re-lease or reboot. Making resolv.conf read-only doesn't work, and using chattr to make it immutable isn't advisable.

Of course you could run static and resolv.conf will be left the way you edit it, but what fun is that? 

I also disable IPV6 globally by running the following as root:
Code:
echo "blacklist ipv6" > /etc/modprobe.d/blacklist

[color=blue]i tried sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist & it said permission denied. i don't have the root acct turned on[/color]

Also try about:config in the adresbar and set the "pipe" maxrequest to 8

then followup by disabling ipv6 in Firefox as well. At this point I just reboot...

if it does not "stick" go to Admin Networking DNS and add the adresses there also.

Hope it helps !

Good luck !

---

### Post by r4ik on 2007-03-18
I doubt if this is going to work.
If i look in my "Networking" the original dns keeps returning.
So there will be no solution for you connecting to Gaim this way.
There must be a more easy way perhaps someone else can help.

---

### Post by lunaz on 2007-03-18
hm, not real sure what to do now, i have to remove the 192.168.0.1 if i want to do anything but browse with firefox.. :(

even windows has it when i do ipconfig /all, but everything connects/works like it's suppose to & i don't understand why & what the difference is.

---

### Post by r4ik on 2007-03-18
Did you try aMSN ?

---

### Post by lunaz on 2007-03-18
no, i can connect to aol, msn & yahoo on gaim ONLY AFTER taking the 192.168.0.1 out of networking > dns. either way i can't seem to see my icq contacts.

i don't understand why that 192.168.0.1 keeps showing up even tho i have both my good dns's in there now.

i can't even update my system until i do this, and i have to do it every reboot.

edit; and why do i have to move all buddies into group root every time i restart gaim? it keeps bringing up old group names i dont want anymore.

---

### Post by r4ik on 2007-03-18
In what order do you're dns's show ?
192.168.0.1 first ?

---

### Post by lunaz on 2007-03-19
192.168.0.1
realdnsaddy

this is on the new comp, i'll get home & do that thing with that file in 9 hrs :P

realdnsaddy1
realdnsaddy2
192.168.0.1

on the old comp i think, but will check it when i get home.

is the router the problem? its a cheap modem router combo: actiontec wireless thingy from qwest. if getting a new one will fix this i'll order today :P

---

### Post by r4ik on 2007-03-19
realdnsaddy1
realdnsaddy2
192.168.0.1

This "should"give you no problems.
Don't know if an other router helps but if you have to buy an Airlive/Ovislink
Just a hint.

Good luck !

---

