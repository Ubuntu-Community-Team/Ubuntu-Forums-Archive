---
title: "Time &amp; date setting problem..."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by jwkungfu on 2008-03-31
Hello,
I am trying to sync my time & date to the internet...
This is the error message...

NTP support is not installed
Please install and activate NTP support in the system to enable synchronization of your local time server with internet time servers.


When I click on the "Install NTP Support" button... nothing seems to happen/work...??

Any tip please?!

john w.

---

### Post by nebu on 2008-03-31
install the ntp server thru synaptic..... it should be available there

---

### Post by Calash on 2008-03-31
This guide is for Feisty, but still seems valid for Gutsy

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Keeping_your_clock_synchronized_with_time_servers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Keeping_your_clock_synchronized_with_time_servers)

---

### Post by jwkungfu on 2008-03-31
> **Calash said:**
> This guide is for Feisty, but still seems valid for Gutsy

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Keeping_your_clock_synchronized_with_time_servers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Keeping_your_clock_synchronized_with_time_servers)

Thanks, I tried thru a terminal window...

john@john-laptop:~$ sudo apt-get install ntp
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ntp has no installation candidate


What now?  ;o/

---

### Post by oldos2er on 2008-03-31
Go to System, Administration, Software Sources, and make sure all repositories are enabled.

---

