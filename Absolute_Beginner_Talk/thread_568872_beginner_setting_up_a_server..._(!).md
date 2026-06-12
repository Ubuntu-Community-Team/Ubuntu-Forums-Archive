---
title: "beginner setting up a server... (!)"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by christapher on 2007-10-06
hello friends,

im completely new to linux (havent even installed it yet actually) and have a few questions before i dive in. i have some entry level c++ from highschool and loads of html and actionscript 2 and 3 experience, so i have knowledge of coding but im a little confused.

my wife just got a mac so i thought it would be fun to toy around and make her HP laptop into a server. first i was going to try osx86 but i thought id do something a little more legal and use linux instead.

heres what i've got to work with:
- an HP Pavillion dv1331se with a broken screen hinge
- ubuntu 7.04 server edition.iso on my mac ready to burn
- this tutorial: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

here are my questions:
- in the tutorial he starts with saying "In this tutorial I use the hostname server1.example.com with the IP address 192.168.0.100 and the gateway 192.168.0.1. These settings might differ for you, so you have to replace them where appropriate." so where do i find out what i should put in those fields? do i just make up an ip address?
-step 10 page 4: what is quota and what does it do?
-stap 13 page 5: what is this and where do i get the info?

thank you guys sooooo much! i know that i totally just bombarded you with stupid questions, but if i could get some help that would be wonderful!

---

### Post by HermanAB on 2007-10-06
Look on your Windoze computer for a clue:
c:\> ipconfig /all

Write down the IP Address, Network Mask, Gateway Address and all DNS addresses in a book.  You'll refer to it many times.

If you have an internet home router, then you can use DHCP to get that information, but you want a server to always use the same address, so it is better to use a fixed address.  There are three ranges of private IP addresses meant for use at home:
192.168.x.y, 172.16.x.y, 10.x.y.z

These addresses are non-routable - in other words if they leak out onto the public internet, then the big Cisco/Nortel switches will drop the packets.

The home router will assign your PCs an address from a pool, commonly 192.168.0.50 to 192.168.0.100.  To  make sure, log onto the router and look at it's settings.  Otherwise, if your wife's PC has an address of 192.168.0.100, then you can make a safe guess that almost anything below 100 is free game, so use 192.168.1.10, for example for your server.

Don't stray 'too far' away from the wife's address (outside the subnet, as controlled by the netmask, hard to explain.).

Ask more questions if you get stuck.

Cheers,

Herman

---

### Post by christapher on 2007-10-06
thank you for that! what about the *server1.example.com* part? i get that server1 is the name i give the computer when i install, but what about *example.com*? do i have to register a domain before i start this process?

---

### Post by HermanAB on 2007-10-06
For starters, leave the machine on your private net.  Only buy a domain name if you wish to run a public server and to do that, you'll have to upgrade your account with your ISP - they will then issue you a static IP address or ten.

So for now, pick anything you want and define it in /etc/hosts:
192.168.0.10 mybox.myhome.net mybox

Also add that entry on the Windows machine in file: c:\windows\system32\drivers\etc\hosts

Now the English domain name will resolve on both machines (but nowhere else).

Cheers,

Herman

---

### Post by HermanAB on 2007-10-06
Note that example.com is a non-resolvable domain name.  So just like the private subnets described above, example.com will be ignored by public name servers.  It is meant for training/testing/examples.

---

### Post by HermanAB on 2007-10-06
By the way, if you are a true beginner, then I strongly recommend *against* installing a server version of Linux.  Rather install regular Ubuntu/Kubuntu/Xubuntu.

The 'server' edition doesn't install the desktop system since it is meant for use unattended in a data centre.  At home (or in a small business) you want the thing to have a desktop and there is really no difference between a server and a desktop system, other than the X windowing system.

Cheers,

Herman

---

