---
title: "ddclient not working :("
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by baz.g on 2008-04-08
i have been able to access my ubuntu 7.10 64 bit machine from remote locations before, after following these instructions in the ubuntuguide wiki:

```

 Maintain Dynamic IP address with ddclient utility

    * Install ddclient from Synaptic Package manager or from the command line: 

sudo apt-get install ddclient

    * Edit the ddclient configuration file: 

sudo gedit /etc/ddclient.conf

    * Place the following in the file: 

protocol=dyndns2
use=web, web=checkip.dyndns.org
server=members.dyndns.org
#
login=my_dyndns_id # (Use the Account Login username you set up at DynDNS)
password='my_dyndns_password' # (Use the Account Login user password you set up at DynDNS)
# (include the quotation marks)
foobar1.dyndns.org # (Use the URL you selected at DynDNS)
# foobar2.dyndns.org # (Use the second URL you selected, if any)
# foobat3.dyndns.org # (Use the third URL you selected, if any)
# fooball4.dyndns.biz # (Use the fourth URL you selected, if any)
# toaster5.homelinux.org # (Use the fifth URL you selected, if any)

    * Restart ddclient: 

sudo /etc/init.d/ddclient restart

```

i am not sure when it stopped working as i hadnt tried it for a little while until today. when i got home from work i ran the command in terminal:

```

sudo /etc/init.d/ddclient status

```

and i get:

```

Status of Dynamic DNS service update utility: ddclient is not running.

```

and if i try to manually start it:

```

bazgrant@bazgrant-desktop:~$ sudo /etc/init.d/ddclient start
bazgrant@bazgrant-desktop:~$ sudo /etc/init.d/ddclient status
Status of Dynamic DNS service update utility: ddclient is not running.
bazgrant@bazgrant-desktop:~$

```

my config file is exactly as per the wiki instructions and, as i said above, it used to work probably a couple of weeks ago since i last tried it.

please help :)

---

### Post by baz.g on 2008-04-10
anybody please?

---

### Post by getglenn on 2008-04-11
have you checked the contents of /etc/default/ddclient

To run ddclient as a daemon, set run_daemon to 'true' in /etc/default/ddclient

---

### Post by baz.g on 2008-04-12
yeh run_daemon is set to "true"

everything is as it was, it used to work but now it doesnt, really wierd.

any other ideas please mate? :)

---

### Post by getglenn on 2008-04-13
g'day baz.g
is your dyndns account still ACTIVE

in  other words it hasnt been closed, cos ddclient hasnt actually been updating the ip addressfor a month and therefore keeping it ACTIVE

just grasping at straws i guess, as you probably have checked but thought i better ask anyway

---

### Post by baz.g on 2008-04-13
yeh it is active, i think that perhaps ddclient is running - to a point - as i have just reinstalled it and in my dyndns account i can see the ip address has just been refreshed, meaning the client has updated to the new dynamic ip.

but if i do:

sudo /etc/init.d/ddclient status

it still says it is not running

wierd :S

---

### Post by getglenn on 2008-04-13
is ddclient listed  in...

System --> Administration --> Services
and
System --> Administration --> System Monitor

---

