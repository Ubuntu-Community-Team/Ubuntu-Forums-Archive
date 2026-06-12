---
title: "Help Udates &amp; Partion Setup Issues"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by zuesko on 2007-02-17
Hi I'm a newbie, what I know about Linux you could write on a pin head. So here are my issues if anyone can help, thanks:) 

1. Tried to update installed programs.

The list of available applications is out of date

download package information

Could not download all repository indexes

[http://easyubuntu.cafuego.net/dists/main/Release.gpg:](http://easyubuntu.cafuego.net/dists/main/Release.gpg:) Could not connect to easyubuntu.cafuego.net:80 (1.0.0.0), connection timed out

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

I did have issue with not been able to acess websites, however from the other posts I found firefox config: IPV6 set disable to true and firefox seems to be Ok.


2. The reason for my update is I want to install partition manager.

Ubutnu is great but as I said I'm no tech and whilest I have Dapper installed on my primary drive, I cannot even see my slave. I do no have any other O/s on this box and do not intend to.
I have tried until I'm blue in the face to follow  terminal line commands to setup drives. I had the same sucess rate   as the U.N. looking for WMD's in Iraqu.

Any assistance would be greatly appreciated 
P.s If anyone can give me the short version on file sturcture and addministative privilles I would be eternally greatful.:KS 


:)

---

### Post by r4ik on 2007-02-17
If your router is using dhcp:

The best bet would be to put your isp's primary and backup dns server addresses in your router's setup page. That way, when /etc/resolv.conf gets overwritten upon re-lease or reboot by dhclient, your isp's dns addresses will be there. Dhclient sometimes stops detecting anything beyond the dns-forwarder in our low-cost routers - but that is a whole different story - not dhclient's fault!)

The other option is to manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

Manually editing addresses in /etc/resolv.conf when you are running dhcp in the router only lasts temporarily as dhclient will overwrite /etc/resolv.conf upon re-lease or reboot. Making resolv.conf read-only doesn't work, and using chattr to make it immutable isn't advisable.

Of course you could run static and resolv.conf will be left the way you edit it, but what fun is that? Smile

I also disable IPV6 globally by running the following as root:
Code:
echo "blacklist ipv6" > /etc/modprobe.d/blacklist


Also try about:config in the adresbar and set the "pipe" maxrequest to 8

then followup by disabling ipv6 in Firefox as well. At this point I just reboot...

if it does not "stick" go to Admin Networking DNS and add the adresses there also.

Hope it helps !

Good luck !

---

### Post by zuesko on 2007-02-18
r4ik Thanks,

edit /etc/dhcp3/dhclient.conf and changed DNS settings as advised. Now have access.

Cheers:)

---

### Post by r4ik on 2007-02-18
Glad it worked.
Thanks for the reply.

---

