---
title: "Still cannot connect to internet"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by kvay101 on 2007-01-21
New to Linux, installed Ubuntu 6.06.1 from CD. Everything seems to work, except I cannot conncet to the internet. I have a router that assigns IP via DHCP and that worked (IP is assigned). My linux machine can see my other Windows boxes, but when I put in an Internet address (Google.com for instance) into Firefox I get "the connection was reset" This happens with name or IP address. I can ping website IPs from terminal command line and get responses. I had this problem with version 5 and forum suggested I upgrade to 6 , so here I am.  I've run out of ideas.

---

### Post by CroEragon on 2007-01-21
You have to give us more information. I assume you connect through network? Can windows PC's connect to Internet? Can you ping with command "ping www.google.com"? Can you open google with typing 72.14.253.99 in browser(Google's IP). Have you tried any other browser ( i suggest konqueror if you have anoter linux box with Ubuntu that have internet, you can use "sudo apt-get -d install konqueror" just to download konqueror, not install it, then burn it or use flash drive to put it on your computer.) Do you connect with ethernet or USB? What is exact name of your router? Have you installed any firewall or reconfigured iptables?

---

### Post by Benchrest on 2007-01-21
Of the several suggestions made above, I would first turn off the firewall if you have one. Did you install Ubuntu with the internet connection hooked up? If you did it should have attempted to configure the internet for you during installation.

---

### Post by phu on 2007-01-21
Hi!):P 

I'm new to ubuntu, and to linux. I've just instaled today ubuntu 6.06. But i can't configure my network settings so i can have internet. On my windows machine i connect to internet through VPN or PPPOE protocol, (with username, password and IP address of the server ).
I've searched for some similar options or something on ubuntu but i couldn't find anything to resemble (VPN or PPPOE).
Can someone help me and tell me what do i have to do to connect to internet.Please.

---

### Post by pebo on 2007-01-21
Have you added your ISP's DNS servers to your network settings?

---

### Post by CroEragon on 2007-01-21
> **phu said:**
> Hi!):P 

I'm new to ubuntu, and to linux. I've just instaled today ubuntu 6.06. But i can't configure my network settings so i can have internet. On my windows machine i connect to internet through VPN or PPPOE protocol, (with username, password and IP address of the server ).
I've searched for some similar options or something on ubuntu but i couldn't find anything to resemble (VPN or PPPOE).
Can someone help me and tell me what do i have to do to connect to internet.Please.Read second and third post. This are general pointer in troubleshooting any problem and you should do as much reading and research as possible before posting and try to help us help you. We are no wizards, we cant read people's mind over Internet. We need info!!!

---

### Post by bradford72 on 2007-01-21
I've had a similar experience, and found that I had to configure my firefox a little bit.

What I had to do was 

1. Open a firefox window and in the URL box (address bar) type in "about:config" (omit the quotes)

2. in the filter box type "network.dns" (again omit the quotes)

3. right click on the value which reads "network.dns.disableIPv6" and select "toggle"...this will change the value from "false" to "true"

4. close firefox, and restart it....you should be on your way

I'm not sure if this is the REAL way to do it, but I couldn't get much on the net myself before I did this, although I was able to ping any site, I couldn't connect...after I did this it worked fine

---

### Post by phu on 2007-01-21
Ok, sorry.
I'm part of a big network that has a server. On windows i connect with ethernet to internet through VPN or PPPOE, i just put there my username, password and the IP address of the server. I don't have an IP ( is automatic ) and i don't know the DNS.
When i installed ubuntu my network cable was plugged in. I can see other computers from my network. 
Thats about everything i can tell you about my situation, hope you can help me.

TY!

---

### Post by kvay101 on 2007-01-21
Here are the answers to questions :
I am conected directly to a router via wired ethernet connection.


Can windows PC's connect to Internet?   Yes - I have 3 windows boxes, no problems



Can you ping with command "ping www.google.com"? yes

Can you open google with typing 72.14.253.99 in browser(Google's IP).  same result

 Have you tried any other browser ( i suggest konqueror if you have anoter linux box with Ubuntu that have internet, you can use "sudo apt-get -d install konqueror"   
I do not have another linux box   I can try download to flashdrive and installing - I don't have time right now, but will try


 Do you connect with ethernet or USB?  ethernet


 What is exact name of your router?   Siemens Speedstream 6520 

Have you installed any firewall or reconfigured iptables?  no


I tried turning ipv6 off within firefox as discribed bewlo, that did not help

---

### Post by zerhacke on 2007-01-21
> **bradford72 said:**
> I've had a similar experience, and found that I had to configure my firefox a little bit.

What I had to do was 

1. Open a firefox window and in the URL box (address bar) type in "about:config" (omit the quotes)

2. in the filter box type "network.dns" (again omit the quotes)

3. right click on the value which reads "network.dns.disableIPv6" and select "toggle"...this will change the value from "false" to "true"

4. close firefox, and restart it....you should be on your way

I'm not sure if this is the REAL way to do it, but I couldn't get much on the net myself before I did this, although I was able to ping any site, I couldn't connect...after I did this it worked fine

This is an improper way of disabling IPv6.  Every other program on your computer that accesses the network will still be IPv6 searching with no IPv6 information.

Instead, open a terminal and type in the following

```
sudo gedit /etc/modprob.d/aliases
```

Those on X/E/Kubuntu will want to substitute gedit for the appropriate text editor of choice.

Find the line: alias net-pf-10 ipv6
Edit this to: alias net-pf-10 off
Save the file and reboot

---

### Post by kvay101 on 2007-01-21
I made the ipv6 change withing aliases.  This did not help.  Problem unchanged.

---

### Post by bradford72 on 2007-01-24
> **zerhacke said:**
> This is an improper way of disabling IPv6.  Every other program on your computer that accesses the network will still be IPv6 searching with no IPv6 information.

Instead, open a terminal and type in the following

```
sudo gedit /etc/modprob.d/aliases
```Those on X/E/Kubuntu will want to substitute gedit for the appropriate text editor of choice.

Find the line: alias net-pf-10 ipv6
Edit this to: alias net-pf-10 off
Save the file and reboot

First off, THANKS for the correction!  I am very new to linux, and sometimes find myself making wild guesses at things!  I did what you suggested, and changed back my firefox config, and things are working great :biggrin:.  Even more fun than figuring out how to make my system work is learning how to do it correctly!  The only difference is my file was in /etc/modprobe.d  Again, a thousand thanks!

---

