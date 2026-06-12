---
title: "sharing internet conection"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Phili on 2008-02-18
Hello,
please excuse me for this simple question. I'd like to share my internet connection from pc1 to pc2, how can I do this? It's a matter of 2-3 clicks in windows, but how does it work in ubuntu?
I've read through numerous threads here and other guides on the internet teaching commandline inputs... They don't work for me.
The first problem is that I'm not sure whether my connection comes from eth0 or eth1. (clicking on the network icon only gives me the brand and specifications of my 2 adapters)
Is there no simple program to do this? 

Thanks!

---

### Post by nilarimogard on 2008-02-18
Here is what i used to share my internet connection:
> The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

---

### Post by Phili on 2008-02-19
That's exactly the solution I find everywhere and which doesn't work for me!
I finally figured out that eth0 is my internet connection and eth1 should share it.

Here's what doesn't work:
1. I'm not sure if # is part of the command (since I have only used the console in windows before and things seem different to me)
2. It says I shouldn't run it with "sudo", if I don't, it says that I don't have enough permissions to use it
3. "echo 1 > /proc/sys/net/ipv4/ip_forward" this line doesn't work at all with and withput sudo I'm lacking permissions
4. when installing the application in step 3, it says that some arichives are missing to install it
5. what does step 7 mean?

Why is there no easier solution? Please help me, I really have a hard time starting with linux, I only manage very basic stuff.

---

### Post by nilarimogard on 2008-02-19
> **Phili said:**
> That's exactly the solution I find everywhere and which doesn't work for me!
I finally figured out that eth0 is my internet connection and eth1 should share it.

Here's what doesn't work:
1. I'm not sure if # is part of the command (since I have only used the console in windows before and things seem different to me)
2. It says I shouldn't run it with "sudo", if I don't, it says that I don't have enough permissions to use it
3. "echo 1 > /proc/sys/net/ipv4/ip_forward" this line doesn't work at all with and withput sudo I'm lacking permissions
4. when installing the application in step 3, it says that some arichives are missing to install it
5. what does step 7 mean?

Why is there no easier solution? Please help me, I really have a hard time starting with linux, I only manage very basic stuff.

1+2+3: I guess you can skip the sudo part and use it, or log in as an admin. # is not part of the command!
4. use: sudo apt-get install <what it says it's missing>
 (without the < >)
5. 7 means you have to edit /etc/sysctl.conf with a text editor and add this line to it: "net.ipv4.ip_forward = 1" (without the quotes). Then save that file.

---

### Post by Phili on 2008-02-19
I found the solution for my problem: ubuntu has problems with one of my network adapters even though it correctly shows it in the network manager.

---

