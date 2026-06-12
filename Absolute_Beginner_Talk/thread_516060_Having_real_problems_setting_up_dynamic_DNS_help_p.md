---
title: "Having real problems setting up dynamic DNS help please"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by safora on 2007-08-02
I'm trying to set up Dynamic DNS; i've tried DDClient and inadyn but not much luck with either. I just dont understand anything :confused::confused::confused::confused:

Can anyone please talk me throgh it?

If so please tell me what chat client I can speak to you on

Thanks in advance for your help :):):)

---

### Post by nexu56 on 2007-08-03
I have been using No-IP for years for my dynamic DNS without problems.

There is a kickass (and strangely amusing) tutorial here: [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

Good luck!

---

### Post by r4ik on 2007-08-03
-

---

### Post by r4ik on 2007-08-03
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

then followup by disabling ipv6 in Firefox as well. At this point I just reboot...

Hope this helps.

---

