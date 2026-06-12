---
title: "Update Client To Map IP Changes"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2007-12-18
Hello

I have downloaded an update client that should run a perl script labeled ddclient in /usr/sbin/ddclient that in turn reads a config file I provided below. 

The purpose of all this it to monitor when my ip address changes and provide the details to the DNS (DynDNS).

When I try and run the pearl script ddclient on the command line in /usr/sbin and press enter, I simply brings up an new command line...when I do a ps -ef | grep ddclient to see if the daemon is running, I dont see anything....do I need to install a Perl deamon ? 



CONFIG FILE

# Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=600
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=your-username
password=your-password
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
example.dyndns.org
custom=yes, example.com


Thanks

---

### Post by MegaJim on 2007-12-19
i am using this tool, and once installed it should start a quick config screen, after following that it adds itself to startup and should constantly run as a process named "ddclient"

it will be in sleep mode for 600 seconds at a time (as expected) but will still run.  great tool.

oh i should mention i used the version from the multiverse repo rather than building it myself so that might be something to try if you got the cvs

---

### Post by hyper_ch on 2007-12-19
I use no-ip.com service for that... their installer is very simply - just in case you won't succeed with your dyndns one.

---

### Post by hyper_ch on 2007-12-19
the no-ip client is in the repositories...

(1) Open an account at no-ip.com and get a subdomain

(2) install the client from the repositories
```

sudo apt-get install no-ip

```

(3) Then you'll be ask for login/pw and presented with a list of subdomains that are registered to that email address

If you are not automatically asked for the configuration details, you can invoke it manuall:
```

sudo noip2 -C

```

For more info use:
```

noip2 --help

```

EDIT: The no-ip daemon will set itself to auto-start and auto-update which is done by the init runlevels.

---

### Post by g2g591 on 2007-12-19
i have ddclient going also (installed from the repos), it works just fine.

---

