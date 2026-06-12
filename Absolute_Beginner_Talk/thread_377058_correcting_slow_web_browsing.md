---
title: "correcting slow web browsing"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by emanuelegarcia on 2007-03-05
Hi,

I installed Ubuntu 6.06 on a Toshiba Satellite laptop and all went well without a hitch except for the fact that web browsing was considerably slower than with MS Windows.

After attempting a few suggested fixes I found that the one that worked was to go to open DNS.  My connection is DSL via a Belkin wireless router.  Simply by changing the DNS settings and following instructions on the openDNS website corrected the problem ([www.openDNS.com)](www.openDNS.com)).

Now there's no reason at all to return to the 'other' operating system.

Hope this helps someone.

EEG

---

### Post by emanuelegarcia on 2007-03-05
Here's the specific link to OpenDNS:

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)


I didn't have to bother with doing anything about the router, simply followed the instructions here, including the following:

If you assign your computer's IP with DHCP, it probably overwrites your /etc/resolv.conf. Here's how to fix that:

Run: sudo gedit /etc/dhcp3/dhclient.conf

Change the prepend line to read:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.

Run: sudo /etc/init.d/networking restart

Using Ubuntu? Check "Networking" to see if the changes applied correctly.
Go to "System –> Administration –> Networking" and click the DNS tab.

---

### Post by jpeddicord on 2007-03-05
OpenDNS servers are great for speeding up DNS searches. However, remember that they do go down occasionally, stopping your connection for the time being. Also remember that it might catch some sites as phishing sites, and sometimes the typo correction goes wonky. It's a great service, but if you get a decent internet speed, don't bother changing your DNS servers.

Your case was different however, so if it provides a noticeable speed boost then by all means go ahead. :-D

---

