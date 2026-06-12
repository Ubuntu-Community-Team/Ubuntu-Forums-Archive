---
title: "opening ports and services"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by none211 on 2007-02-03
i was hoping someone could help me by telling me how to open ports and start services on them. i would like to open telnet and ftp so that I can do a couple things from a remote location.

---

### Post by pseudonym on 2007-02-03
Ubuntu (and all Linux distros) come with a built in firewall called iptables. But it's not easy to configure. Instead, what you should install is a good frontend to iptables like [Firestarter]("http://www.fs-security.com/"). You can use this to open ports on your machine/network and allow connections to running services.

As far as telnet and ftp is concerned, you'll need to install server programs for each (I think clients for both are installed by default). I don't use telnet (it's insecure) but for ftp I use [wu-ftpd]("http://www.landfield.com/wu-ftpd/"). There's also [vsftpd]("http://vsftpd.beasts.org/") and a few others. All programs I've mentioned can be installed via apt-get, Synaptic, or Add-Remove.

HTH

---

### Post by none211 on 2007-02-03
excuse me if i'm asking stupid questions, but allowing a connection to a certain port (telnet) through ip chains, using the firestarter front end dose't start the daemon on that port... right? my question remains and excuse me if i'm aksing somehting that's already answered, but how do i start the service, or control the daemon in linux?

---

### Post by pseudonym on 2007-02-04
No, Firestarter allows you to control ports, but doesn't start the services running on them. Most of these services are started like so - ```
sudo /etc/init.d/service_name start
``` The documentation for each service will tell you more but that's the basic command. Typing - ```
sudo /etc/init.d/service_name -help
``` will get you the list of available options (like 'start' 'stop' or 'status').

There will also be a configuration file for each server program which allows you to fine tune your configuration and will probably also need to be edited to allow the service to run at all, since outward looking network services are not enabled by default in Ubuntu. But you will need to refer to each server's documentation for this.

---

