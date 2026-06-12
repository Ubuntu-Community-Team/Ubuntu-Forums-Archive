---
title: "Setting Up Ubuntu Edgy Eft Netboot - PXE Server - Unable to Connect to Internet"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by DigitalDaiquiri on 2006-12-27
After trying to install Ubuntu on a laptop without a CD-ROM or floppy drive I came across the idea of setting up a preboot execution environment server from which I could install Edgy over my network.  I started by following the following guide: [http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server")  

Being relatively new to Linux, and this being my first server experience I ran into a problem on the "Setting Up A PXE Install Server For Multiple Linux Distributions With Ubuntu Edgy Eft" guide on page 2 ([http://www.howtoforge.com/ubuntu_pxe_install_server_p2]("http://www.howtoforge.com/ubuntu_pxe_install_server_p2")). Everything seemed to be going fine as I followed the steps through the first 3 pages of "The Perfect Setup - Ubuntu 6.10 Server (Edgy Eft)" guide ([http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3")) as directed by the article. Mind you I have almost no experience with network topology, I'm just beginning to learn about things such as DNS, and DHCP. Not understanding exactly what to do I edited my "/etc/network/interfaces" file to match the one on page 3 step 5 (Configuring the Network) of the 6.10 server guide. I thought everything went smothly (although I didn't edit it to specifically fit my network information but rather used the information in the provided example. This statement is also true in regards to editing my "/etc/hosts" file (I kept the example.com).

I continued on to page 2 of the PXE article and became stuck on step 4, "Set Up Ubuntu Edgy Eft Netboot". For some reason I am unable to download the needed files and am stuck with the following readout "open 'archive.ubuntu.com' [Resolving host address...]. I believe that I'm not getting a connection to the internet for some reason but I'm not sure.

A friend of mine mentioned that I may need to use my own IP address and gateway instead of using the example in the guide.  After looking on [www.google.com/linux](www.google.com/linux) and [http://en.wikipedia.org/wiki/Ifconfig](http://en.wikipedia.org/wiki/Ifconfig) I came to the conclusion that the Linux equivalent of Windows NT's "ipconfig" is "ifconfig". After typing "ifconfig" on the command line I received a readout that listed my IP address, mask, etc. I don't know if this tool is just displaying the contents of the "/etc/hosts" file I edited earlier, or if it is instead giving an accurate readout of my network. Is there any other way to go about finding the IP address and Gateway information for my network?

I sincerely appreciate everyones time and help! :)

---

### Post by DigitalDaiquiri on 2006-12-27
I found a thread concerning the same type of difficulties I'm having with my DNS: [http://www.linuxforums.org/forum/redhat-fedora-linux-help/30054-configuring-dns.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/30054-configuring-dns.html")


My "/etc/ resolv.conf" file reads the following:
```
search *my last-name*
nameserver 192.168.2.1
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187
```

and my "/etc/hosts" looks like this:
```
127.0.0.1    localhost.localdomain localhost
127.0.1.1    ubuntu-6.10-pxe-install-server.example.com ubuntu-6.10-pxe-install-server


# The following lines are desirable for IPv6 capable hosts
::1    ip6-localhosts ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

If I try to ping google I get the following error:
```
ping: unknown host google.com
```

The thread suggests typing the following command: ```
dig www.google.com
```
To which I receive: 
```
; <<>> Dig 9.3.2 <<>> www.google.com
;; global options;  printcmd
;; connection timed out; no servers could be reached
```

...and ```
ifconfig | grep 'inet addr'
``` to which I get the following:
```
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
inet addr:127.0.0.1 Mask:255.0.0.0
```

The thread suggested deleting all of the lines from "/etc/resolv.conf" and replacing them with ```
nameserver 127.0.0.1
```  This didn't solve the problem so I then followed the suggestion to type ```
netstat -an | grep ':53'
``` This in turn didn't give a readout. (Mind you the thread was written concerning RH9.0, so that might explain the lack of a response from the last command).  The thread then recommended service commands such as "service iptables stop" that are not Ubuntu native.  I appreciate everyone for their time, and I hope this at least helps to give an idea of what may be going wrong.

---

