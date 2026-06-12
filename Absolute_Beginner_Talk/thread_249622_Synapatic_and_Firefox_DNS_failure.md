---
title: "Synapatic and Firefox DNS failure"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by peterrdrake on 2006-09-02
Hi All

I new to Ubuntu but but not to Unix  I installed Ubuntu 6 yesterday and connot seem to get Synapatic to connect to any repostories.  Also firefox will not resolve domain name but will connect by IP

The Networking setting GUI shows the DNS as my router (a DLink DSL-504T).  I have tried entering my ISP's DNS manually (using the Networking GUI) but that didn't seem to change anything, even when I rebooted.

Any suggestion would be great

Cheers Peter

---

### Post by furiousV on 2006-09-03
Usually simply rebooting your router will fix that, though temporarily.

I get that all the time, sometimes it lasts for 10 minutes and then I will need to reboot, sometimes a week. I think it depends on how aggressive you are using bit torrent.

Have your PC use your router as the DNS server, and in the router, configure it to use 4.2.2.2 and 4.2.2.3 for manual DNS servers. That might help.

---

### Post by nrwilk on 2006-09-03
This is a common problem in Dapper (v6.06).

The file which contains your DNS info is /etc/resolv.conf .  You can temporarily fix the issue by replacing the line with the address to your router to your correct DNS IP.

This issue is caused because some routers try to be DNS servers for their internal network, and so they broadcast their own IPs as IPs to correct DNS servers.

There are several threads around with many replies talking about the issue, but I finally found the answer in the last post here:
[http://www.ubuntuforums.org/showthread.php?t=134731](http://www.ubuntuforums.org/showthread.php?t=134731)

If you're on a desktop where you'll always be using the same network, you can just stop using DHCP and assign static information for the computer.  That works for me on my desktop.  But, on my laptop I couldn't do that because I'll be using it on many different networks.

So, as it says in that thread which I linked to above, just add a line like the following to your /etc/dhcp3/dhclient.conf file:
```
prepend domain-name-servers <dns-server1>, <dns-server2>, <dns-server3>;
``` 
That will always stick the addresses you specify on that line into you /etc/resolv.conf file.  It may make it so that a line or two end up being duplicated, but this does not make a difference.  At least it will work.


I hope this helps.  Post more to let us know how it's going. :)

nrwilk

---

