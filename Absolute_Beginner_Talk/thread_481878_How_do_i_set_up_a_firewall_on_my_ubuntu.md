---
title: "How do i set up a firewall on my ubuntu"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by cheboingboing on 2007-06-23
can anyone give a step by step guide to set a firewall on ubuntu.

---

### Post by Gael05 on 2007-06-23
Hi.... I konow only 2 firewalls for linux....
First, there is firestarter and the guard dog...
Personnaly, I usy firestarter...
Go to applications, add/remove, and then in search, type firestarter....
Click in the box, and press apply....

---

### Post by swoll1980 on 2007-06-23
there is a firewall installed by default called ip tables all ports are closed by default
you can download a graphical tool to configure ip tables I use firestarter
open a terminal and enter this command
sudo aptitude install firestarter

---

### Post by swoll1980 on 2007-06-23
in order  to configure firestarter you have to be the root user in order to do this open a terminal and enter the command 
sudo firestarter

---

### Post by cheboingboing on 2007-06-23
thank you thank you the only problem is i get this what is this.

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster

---

### Post by swoll1980 on 2007-06-23
What did you do to get that error?

---

### Post by cheboingboing on 2007-06-23
now i get that my internet setting are not ready so it wont let me start the firewall

---

### Post by cheboingboing on 2007-06-23
ok got it i fixed it thank you for the help

---

### Post by swoll1980 on 2007-06-23
are you on a home network or is it just the one pc?

---

### Post by cheboingboing on 2007-06-23
well earlier i had tried to install the cluster manager and it gave me that error and then when i tried installing lime wire along with java. also i tried to install divx cause i needed a codec but then i figuered out an easier way. it could have been any number of those things i dont really know but now everytime i install something it pops out. most of the time though the installation goes ok.

---

### Post by penguin007 on 2007-06-25
This script will drop all unsolicited incoming packets but allow outgoing traffic to innitiate connections. Note you must run it as root (i.e. sudo)

Air tight for home users on a single PC.


# Check that user is root
if [ "`whoami`" != "root" ]; then
    echo
    echo "** Error **"
    echo "You need to be 'root' "
    echo
    exit
fi
iptables --flush
iptables --flush -t nat
iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP
iptables -A OUTPUT -j ACCEPT -o lo
iptables -A INPUT -j ACCEPT -i lo
iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

---

### Post by John.Michael.Kane on 2007-06-25
This may be of use.
[HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661&highlight=iptable")

---

