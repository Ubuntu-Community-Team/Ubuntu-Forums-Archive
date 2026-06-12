---
title: "Hostname basics and relating them to Windows"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by aglide on 2007-09-17
My network at work is pretty much all windows machines, and I've added an ubuntu box that I've assigned a static IP to.

In windows, if a machine is named "WINDOWS1" during setup, then joined to our domain, the "full computer name" in windows becomes "WINDOWS1.pla.corp.net".

When setting up the ubuntu box, I chose "KCMOAPPKB1" for the hostname. I don't plan on doing anything like joining the domain, but I am going to have our network team add a DNS entry to get "kcmoappkb1.pla.corp.net" to resolve to the IP of the ubuntu box.

In this situation do I need to change the hostname on the ubuntu box from "KCMOAPPKB1" to "kcmoappkb1.pla.corp.net" in /etc/hosts and /etc/hostname?

How exactly does the "pla.corp.net" suffix come into play on the ubuntu box in this situation?

---

### Post by yabbadabbadont on 2007-09-17
```
/home/daffy $ hostname
yoiks
/home/daffy $ dnsdomainname 
and.away
/home/daffy $ cat /etc/hostname 
yoiks
/home/daffy $ grep yoiks /etc/hosts
127.0.1.1       yoiks.and.away  yoiks

```
The rest is left as an exercise for the student.  :D

---

### Post by bodhi.zazen on 2007-09-17
You can set your hostname to anything you wish on a private network.

The hosts file is used, on both Windows and LInux, to look up host names.

Your computer will look there first, think of it as an address book

The file is /etc/hosts and the format is :

<IP_Address> <hostname>

So you could add :

<ubuntu_IP_Address> KCMOAPPKB1 

To your windows hosts.

You need to edit a few files to change your hostname, and you need to be careful or you will loose access to sudo :twisted:

Go to : General Tab -> Host Settings -> Hostname Enter (change) the computer name if you like.

Reboot ...

Else you need to edit both /etc/hostname and /etc/hosts

---

### Post by aglide on 2007-09-17
Thanks for the replies so far.

yabbadabbadont:

This is the first I've heard of the "dnsdomainname" command/property. I'm researching it now and will post again when I get stuck :)

bohdi.zazen:

Our network has thousands of users, all of which run Windows. I'm going to have our network admins add an entry for this machine on the DNS servers their windows boxes all use for name resolution. My goal is for them to be able to run "ping kcmoappkb1" in windows and get it to resolve and reply. When they do this their machines will append .pla.corp.net to the name and then resolve to the IP.

I should add that this is Dapper 6.06 server and there no GUI installed. Thank you for the warning about potentially losing access to sudo!

---

### Post by aglide on 2007-09-17
Okay, I tried running the dnsdomainname command and got no output, so I've modified the 127.0.1.1 line in /etc/hosts:

127.0.1.1 KCMOAPPKB1.pla.corp.net KCMOAPPKB1

And now dnsdomainname outputs "KCMOAPPKB1.pla.corp.net".

My next question: is the hostname KCMOAPPKB1 case sensitive? Is there any risk in modifying /etc/hostname and /etc/hosts to change KCMOAPPKB1 to all lowercase?

---

### Post by bodhi.zazen on 2007-09-17
> **aglide said:**
> Okay, I tried running the dnsdomainname command and got no output, so I've modified the 127.0.1.1 line in /etc/hosts:

127.0.1.1 KCMOAPPKB1.pla.corp.net KCMOAPPKB1

And now dnsdomainname outputs "KCMOAPPKB1.pla.corp.net".

My next question: is the hostname KCMOAPPKB1 case sensitive? Is there any risk in modifying /etc/hostname and /etc/hosts to change KCMOAPPKB1 to all lowercase?

I believe it is case sensative, but I am not 100%.

As long as you are consistent and modify both as the same time you should be ok.  If you make a mistake, you can recover from the recovery mode or a live CD.

---

### Post by yabbadabbadont on 2007-09-17
> **bodhi.zazen said:**
> I believe it is case sensative, but I am not 100%.

As long as you are consistent and modify both as the same time you should be ok.  If you make a mistake, you can recover from the recovery mode or a live CD.

A quick test:
```
/home/daffy $ ping -c 1 yoiks
PING yoiks.and.away (127.0.1.1) 56(84) bytes of data.
64 bytes from yoiks.and.away (127.0.1.1): icmp_seq=1 ttl=64 time=0.100 ms

--- yoiks.and.away ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.100/0.100/0.100/0.000 ms
/home/daffy $ ping -c 1 YOIKS
PING yoiks.and.away (127.0.1.1) 56(84) bytes of data.
64 bytes from yoiks.and.away (127.0.1.1): icmp_seq=1 ttl=64 time=0.099 ms

--- yoiks.and.away ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.099/0.099/0.099/0.000 ms

```
Doesn't seem to be case sensitive.  ;)

---

### Post by bodhi.zazen on 2007-09-17
Cool. 

GooGlE.Com even works !

---

