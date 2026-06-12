---
title: "configuring ethernet interfaces through command ilne"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by kurian on 2008-03-01
hi,
please do answer my doubts

1. I have a linux machine ....i need to know how to change the ip
address and subnet mask through the command line...????
2. I also need to how to configure the ethernet interface for dhcp this to in command line???

---

### Post by Cypher on 2008-03-01
1. For one time change do
```

sudo /sbin/ifconfig eth0 netmask <ip> netmask 255.255.255.0

```
If you want to change it permanently, then look into /etc/network/interfaces and enter
```

auto eth0
iface eth0 inet static
address <IP>
netmask <netmask>
gateway <gateway>
broadcast <broadcast>

```

2. Once again, for one time do
```

sudo dhclient eth0

```
For long term, modify the /etc/network/interfaces and the text would be
```

auto eth0
iface lo inet dhcp

```

---

### Post by lloyd_b on 2008-03-01
> **kurian said:**
> hi,
please do answer my doubts

1. I have a linux machine ....i need to know how to change the ip
address and subnet mask through the command line...????
2. I also need to how to configure the ethernet interface for dhcp this to in command line???
 
1.  "man ifconfig" in a terminal window.  This command allows you to change the configuration of the interface (IP address, netmask, etc).  Be advised - if you change the IP of the interface, you may also need to change some routes ("man route" in a terminal window).  Also be aware that you'll need a "sudo" to actually make changes to either the interface or the routes.

2.  That one's different.  Determining whether or not to use DHCP is controlled via the file "/etc/network/interfaces".

Could you describe what it is you're trying to accomplish?  Knowing this will make it easier to determine the best way to accomplish the task.

Lloyd B.

---

### Post by kurian on 2008-03-02
First of all thanks for the reply......

my aim is to configure the interface of an embedded linux development kit....

iam having a development kit for avr32 processor which has got a linux in it....i want it to get connected to the net in my college which needs configuring static ip addresss ...

regards

---

### Post by lloyd_b on 2008-03-02
> **kurian said:**
> First of all thanks for the reply......

my aim is to configure the interface of an embedded linux development kit....

iam having a development kit for avr32 processor which has got a linux in it....i want it to get connected to the net in my college which needs configuring static ip addresss ...

regards

One reasonably easy solution:

1.  Set up for DHCP.
2.  Copy the file "/etc/network/interfaces" to a new name ("/etc/network/school", for instance)
3.  Modify this copy for the appropriate static IP

When you boot the system, it'll initially try DHCP.  But when at school, all you need to do is (at a command line):
```
sudo ifdown eth0
sudo ifup -i /etc/network/school eth0
```
(Note: depending on your PATH, you may or may not need "/sbin/" in front of the ifup/ifdown commands).

And then to make it even easier, create a script called "school" containing those commands, and then "sudo school".

Lloyd B.

---

### Post by kurian on 2008-03-02
Didnt understand could you please explain....

---

### Post by lloyd_b on 2008-03-02
> **kurian said:**
> Didnt understand could you please explain....

1.  Modify the file "/etc/network/interfaces" to use DHCP.  You can do this (if it is not already set up this way) by having the lines
```
auto eth0
iface eth0 inet dhcp
```
in that file.

2.  Copy the interfaces file:
```
sudo cp /etc/network/interfaces /etc/network/school
```

3.  Edit the file "/etc/network/school" for a static IP.  Change
```
iface eth0 inet dhcp
```
to
```
iface eth0 inet static
     address <School IP Address>
     netmask <School Netmask>
     gateway <School gateway address>
     broadcast <School broadcast address>

``` filling in the <...> items with the proper information.

Then use the commands in the previous post to switch from DHCP to static IP (when at school).

To create a script, just edit a file (named "school"):
```
#!/bin/bash

/sbin/ifdown eth0
/sbin/ifup -i /etc/network/school eth0

```
Then:
```
chmod 700 school
```
to make it executable.

I would suggest moving the script to somewhere in your PATH ("/sbin" is the most reasonable location for this type of script), and using 
```
sudo chown root /sbin/school 
```
to change it's owner to root.  Once you've done this, 
```
sudo school  
```
should be all that's required to enable a static IP configuration when at school.

Lloyd B.

---

