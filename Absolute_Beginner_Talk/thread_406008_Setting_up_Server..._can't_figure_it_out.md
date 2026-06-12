---
title: "Setting up Server... can't figure it out"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Torahteen on 2007-04-10
Hello all, once again.

I have ubuntu-server installed without LAMP or anything but the base system installed on it. I'm trying to get a typical server set up on it, and decided that I didn't wanna mess around with pre-installed LAMP packages. I install Edgy, and am now following this tutorial: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3) to set up OpenSSH. Problem is, that I'm sure that this isn't gonna work for my system as is. So, I ask if any of you linux experts could tell me what I need to change in order for this to work, and for me to access the computer from another computer with Putty or likewise.

Here's my configuration. I have the server computer running through a router that I access with the IP of 192.168.1.1. The installation has the computer set up with DHCP, which apparently I don't want for a server. As of now, if I check the LAN IP of the server, I get 192.168.1.106.

I downloaded the package ssh openssh-server with apt-get. So I have that installed, but what do I do now?

BTW, I did try this already, with no success. Just don't know what I should use in the config files to make it work with my system.:confused:

---

### Post by Torahteen on 2007-04-10
Ok... Apparently OpenSSH got set up correctly. However, I'm confused about how to set up my network interfaces file. For instance, the tutorial I'm using said to add something like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

eth0 is the device I'm using. But what should I replace everything else with? Rather, what's important to make sure is correct in order for me to use my router correctly? As stated before, the address to my router is 192.168.1.1, and the address of the server is 192.168.1.106, or at least that's how I reach it to log in with Putty (SSH).

Also, I was suppose to edit /etc/hosts and put something like this:

```
127.0.0.1       localhost.localdomain    localhost
192.168.0.100   server1.example.com      server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

What exactly is the domain name for? And is IPv6 the correct protocol to use? Or should I use IPv4? I appologize for all the questions... I'm a quick learner I swear! :P Thanks for the help in advance.

---

### Post by annda on 2007-04-10
of course, you will have to change 192.168.0.100 with 192.168.1.106 for address, 192.168.0.1 for 192.168.1.1 for gateway and 192.168.0.0 for 192.168.1.0 for network - but you have probably figured that out already.

if you do not have a registered domain, the domain name is simply the name of your computer.

also, remember that the 192.168.x.x IP is internal to your home network. you will not be able to ssh to your computer from the outside world using this IP (in case you want to).

---

### Post by Torahteen on 2007-04-10
Thanks a lot... I'll try everything you said. I had gotten 2/3 IP numbers correct lol. I knew what gateway and address were, didn't understand the other. As for the domain, I can just put:

192.168.1.106   linserver      server

If linserver is the name of my server? Or...

Edit: Oh, and when I decide to make the server public, can I just change the address to my network's IP address? Or would I get set up with a DNS and then use my actual domain with the same IP address above?

---

