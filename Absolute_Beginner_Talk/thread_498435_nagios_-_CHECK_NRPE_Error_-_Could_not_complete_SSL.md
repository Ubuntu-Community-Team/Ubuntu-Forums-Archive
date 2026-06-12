---
title: "nagios - CHECK_NRPE: Error - Could not complete SSL handshake"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-07-11
having issues with my nagios NRPE install 

trying to test my install and i am havin ssl issues:
```
/usr/local/nagios/libexec/check_nrpe -H localhost -c check_users 
```

and i get the following spit out at me:

```
CHECK_NRPE: Error - Could not complete SSL handshake.
```

the nagios site states
> 
   1. Different versions. Make sure you are using the same version of the check_nrpe plugin and the NRPE daemon. Newer versions of NRPE are usually not backward compatible with older versions.
   2. SSL is disabled. Make sure both the NRPE daemon and the check_nrpe plugin were compiled with SSL support and that neither are being run without SSL support (using command line switches).
   3. Incorrect file permissions. Make sure the NRPE config file (nrpe.cfg) is readable by the user (i.e. nagios) that executes the NRPE binary from inetd/xinetd.
   4. Pseudo-random device files are not readable. Greg Haygood noted the following... "After wringing my hair out and digging around with truss, I figured out the problem on my Solaris 8 boxen. The files /devices/pseudo/random* (linked through /dev/*random, and provided by Sun patch 112438) were not readable by the nagios user I use to launch NRPE. Making the character devices world-readable solved it."
   5. Unallowed address. If you're running the NRPE daemon under xinetd, make sure that you have a line in the xinetd config file that say "only_from = xxx.xxx.xxx.xxx", where xxx.xxx.xxx.xxx is the IP address that you're connected to the NRPE daemon from. 


but i am not sure about how to test for those problems...

any ideas on this... i compiled using the instructions on nagios.sourceforge.net/docs/nrpe/NRPE.pdf

thanks!

---

### Post by xang on 2008-01-08
Did you compile nagios from source? If you did, you must compile it with the SSL option. Otherwise, use the undocumented -n flag.

ex. 


/usr/local/nagios/libexec/check_nrpe -n -H localhost -c check_users


And...

/usr/local/nagios/nrpe -n -c nrpe.cfg -d (if running in daemon mode).

HTH.

Xang.

---

### Post by byunique on 2008-01-28
[SIZE="3"]Ok, I was working on the same thing. CentOS as the monitoring server and Ubuntu Gutsy Gibbon as the client. I am using CentOS to monitor Ubuntu Client.

First thing I installed the nagios-nrpe-plugin, thinking that would be the client, but thats not the right package if you look at the description...

1) Installed the nagios-nrpe-server,  per Synaptic.
2) netstat -an | grep 5666, verified process was running
3) on Nagios Host, ran :
/usr/local/nagios/libexec/check_nrpe -H 10.0.0.6
CHECK_NRPE: Error - Could not cocmplete SSL handshake.

4) tweaked the Ubuntu's nrpe config:

 vi /etc/nagios/nrpe.cfg

allowed_hosts=127.0.0.1 
to
allowed_hosts=10.0.0.5 (my Nagios host IP)

This is needed since the nagios plugin was installed w/o inetd/xinetd.

5) restarted nagios plugin:

/etc/init.d/nagios-nrpe-server restart

5) Tested Again:

/usr/local/nagios/libexec/check_nrpe -H 10.0.0.6
--> NRPE v2.8.1


:)[/SIZE]

---

