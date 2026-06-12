---
title: "help with virtualbox bridging"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-09-27
I am following the guide found below:
[PHP]nstall the required packages -

    sudo apt-get install uml-utilities bridge-utils

Step 2 :
Create TAP interface -

    sudo tunctl -t tap1 -u samiux

** where “samiux” is the username of your Ubuntu (here is my name)

Step 3 :
Create a br0 bridge -

    sudo brctl addbr br0

Step 4 :
Make your real network interface be promiscuous -

    sudo ifconfig eth0 0.0.0.0 promisc

Step 5 :
Link your real network interface to bridge br0 -

    sudo brctl addif br0 eth0

Step 6 :
Assign an IP to the br0. If you are using DHCP -

    sudo dhclient br0

Or, if you assign an IP yourself -

    sudo ifconfig br0 192.168.1.102

* the IP may be different from yours.

Step 7 :
Link TAP to bridge br0 -

    sudo brctl addif br0 tap1

Step 8 :
Activate TAP interface -

    sudo ifconfig tap1 up

Step 9 :
Change the permission of /dev/net/tun -

    sudo chmod 0666 /dev/net/tun

Step 10 :
At the VirtualBox startup panel, choose “Host Interface” and add “tap1&#8243; to “Interface Name”.

Step 11 :
At the guest (after boot up the guest OS), change the IP of the guest OS to the same subnet of your host.

    IP 192.168.1.200
    netmask 255.255.255.0
    gateway 192.168.1.1
    DNS #1 208.67.222.222
    DNS #2 208.67.220.220[/PHP]

I am fine until step 4. I am assuming I want to use my real static IP address here instead of 0.0.0.0.
Also, on step 6, am I assigning the real static Ip of my host machine (192.168.1.101), or am I setting the IP for the guest - so something like 192.168.1.102? If so, why does the guest show the IP as 192.168.1.200 instead of what is was assigned?

---

### Post by bodhi.zazen on 2007-09-27
Step 4 ~ No, use 0.0.0.0 (not your IP address)

Setp 6 ~ You are setting the IP address of the bridge, or HOST ether net card. You set the guest IP on the guest (this obviously depends on guest OS).

---

### Post by jba6511 on 2007-09-27
when I do the steps posted below everything works great. I can ping the machine from another pc on my network and share files between the two. However, I loose all network connectivity on my host (can not ping, browse online, see other hosts, etc). What am I doing wrong? I use eth2, another nic card, since my eth1 is the onboard nic with the gigabyte 965p s3 that is not supported. I am choosing host networking with the name tap1 and setting the ip to 192.168.1.104. The ip of the host is 192.168.1.101. I want to be able to have connectivity on the host and the guest, and have the host be able to share files, ping, etc the guest.

[PHP]blake@e6300:~$ sudo tunctl -t tap1 -u blake
Password:
Set 'tap1' persistent and owned by uid 1000
blake@e6300:~$ sudo brctl addbr br0
blake@e6300:~$ sudo ifconfig eth2 0.0.0.0 promisc
blake@e6300:~$ sudo brctl addif br0 eth0
interface eth0 does not exist!
blake@e6300:~$ sudo brctl addif br0 eth2
blake@e6300:~$ sudo ifconfig br0 192.168.1.101
blake@e6300:~$ sudo brctl addif br0 tap1
blake@e6300:~$ sudo ifconfig tap1 up
blake@e6300:~$ sudo chmod 0666 /dev/net/tun[/PHP]

---

### Post by jba6511 on 2007-09-28
bump

---

### Post by bimmerd00d on 2007-10-02
Thanks for this, it helped quite a bit.  Also, your ethernet card will be supported in the gutsy kernel.  You can upgrade to that now if you want, there's another thread.  I have the same NIC in mine and it works like a charm :)

---

### Post by jba6511 on 2007-10-02
thanks. I was hoping they would add that support

---

### Post by azmodie on 2007-10-03
I tried to follow this post but could not get the vm to boot. kept getting error saying could not init host network interface  or something like that.  

this post [http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)  has these commands
```
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.0.45 dev tap0
sudo arp -Ds 192.168.0.45 eth0 pub
```

which i believe are from the man page for 'tunctl' 
this fixed the issue and host bridge netwroking works fine now.

---

### Post by bimmerd00d on 2007-10-04
how can i make this all work upon boot?  Mine seems to lose its settings when i reboot. :confused:

---

### Post by bodhi.zazen on 2007-10-04
> **bimmerd00d said:**
> how can i make this all work upon boot?  Mine seems to lose its settings when i reboot. :confused:

Put your commands in /etc/rc.local

---

