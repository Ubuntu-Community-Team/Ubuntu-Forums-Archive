---
title: "Nagios - Adding Remote Machines To Monitor"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-07-11
Need to add a remote host to my nagios server... Where does that info go...  I was fooling around with the minimal.cfg but not joy...  pls advise...

---

### Post by upbeat.linux on 2007-07-12
To configure Nagios properly requires careful reading of the documentation.  Although there are a few GUI's out there as well as repackaged versions that make it easier to start and configure Nagios, however I suggest starting with a text editor to get it up and running.

To add servers to your Nagios config you'll have to do the following:

1. In /etc/nagios/contacts.cfg you will need to configure contacts for the Nagios to notify in "emergencies"
2. In /etc/nagios/contactgroups.cfg you will add contacts to contact groups. For instance, you could have a Linux contact group as well as a Microsoft Exchange contact group which contain similar or complete different members.
3. In /etc/nagios/hosts.cfg you will define the hosts (or systems) you want to monitor
4. In /etc/nagios/hostgroups.cfg you will define the host groups that each host belongs too. Again, think MySQL servers, Microsoft Exchange, SAN servers, etc....
5. In /etc/nagios/services.cfg you define the services that are monitored on each host.  At the end of your service definition you will see "check_command".  This defines what commands you use to check the service on your host and can be defined with (see next step)
6. /etc/nagios/checkcommands.cfg - Feel free to customize if you are not using a default checkcommand

Again, Nagios documentation although long-winded is extremely helpful.....

Cheers...

---

### Post by huggy77 on 2007-07-13
thankyou sir - that was perfect... i found the syntax for addng machines but  i could not for the life of me figure out where to put the host information...

i am not using a GUI - i find i learn more using VIM

thanks again.

---

