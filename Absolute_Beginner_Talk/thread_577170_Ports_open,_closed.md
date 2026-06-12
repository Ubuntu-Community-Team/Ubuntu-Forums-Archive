---
title: "Ports open, closed?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-10-15
I've been browsing the forums trying to find out how to open ports in the terminal. Some of the posters say that all the ports are closed by default, some say they are all open. How do I know who to believe? Either way no one seems to know how to open a port with out using firestarter. Is there a way to check on the status of a port from the command terminal, and open or close it respectively?

---

### Post by jbrown96 on 2007-10-15
All ports are closed by default on Ubuntu. There are two or three that are open but only to the local host - no one can initiate a connection to you on those ports. 
Nmap is a very good tool to scan ports. You can get it through Synaptic/Adept and there are several GUIs for it (I use NmapFe). Do a Syn scan on all ports on your machine. It should be set to scan you by default (127.0.0.1 I think). 
I'm not sure about how to open ports.

---

### Post by RomeReactor on 2007-10-15
Hi. You can use [iptables]("https://help.ubuntu.com/community/IptablesHowTo") to configure firewall rules through the terminal; iptables is already installed on your system.

To scan for open ports at any given time, you can use [netcat]("http://netcat.sourceforge.net/"), which is also installed:
```
nc -z -v -w2 127.0.0.1 1-65535
```
or
```
nc -z -v -w2 localhost 1-65535
```

Alternatively, you can use [nmap]("http://insecure.org/nmap/"). Look for nmap in Syanptic; or to install it from the command line:
```
sudo apt-get install nmap
```
And once it's installed:
```
sudo nmap -v -p- 127.0.0.1
```
or
```
sudo nmap -v -p- localhost
```

---

