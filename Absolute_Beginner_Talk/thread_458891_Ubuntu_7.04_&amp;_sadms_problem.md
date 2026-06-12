---
title: "Ubuntu 7.04 &amp; sadms problem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Darthter on 2007-05-30
mornin' folks....

Bit of a noobie with Linux in general.....but getting there.

Having a problem getting sadms setup on Ubuntu 7.04 so that I can authenticate to my windows 2000 domain.

All my setting validate as OK, but when I hit the "Install" button, I get the following msg:

Invalid configuration.  Exiting....
[ERROR]
returned error code 7
command line was <./_install.sh  'domain.local' 'DNS IP' 'DC server name' 'domain' 'amcintosh-desktop' 'Computers' 'administrator' '*****' 'Domain Users' 'host address' 'wins address'>

Any ideas what could be the problem???

---

### Post by teamanx on 2007-05-31
Well, there are some things you should check on the Network Setting dialog (System>Administration>Network):

- Go to the "Connections" tab, click on the wired connection and then click on "Properties". Then, in "Configuration" select "static IP adress", and then fill the rest of the fields. This will prevent DHCP from overriding any of our settings.

- On the "General" tab, make sure the host and domain name are the same that you are entering in SADMS.

- If your local domain name ends with ".local", then it is making a conflict with the Avahi daemon, which is used for automatic net service discovery. Uncheck "Automatic service discovery" to disable it.

- On the "DNS" tab, make sure you have the right DNS server, and your local domain name is under "Search domains".

- On the "Hosts" tab, there must be an entry that looks like this:

IP Address   |  Aliases
127.0.1.1     |  myhostname.mydomain        myhostname

(Replace "myhostname" and "mydomain" with your host and domain names. The name of your host with ".mydomain" must be before the name of the host alone).


Then close the dialog, and reboot your computer. Try to ping the FQDN of your local AD server ("ping myserver.mydomain", not just "ping myserver"). If you get a response, SADMS should work now. Make sure you are entering on the "KDC" field the hostname of your server, not the IP address.

Let us know if the problem has solved. Regards.

---

