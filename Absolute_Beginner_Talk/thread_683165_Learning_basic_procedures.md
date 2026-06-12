---
title: "Learning basic procedures"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by doondoon on 2008-01-30
I am trying to get Kismet working on my HP dv5000.The wifi is working fine and I can detect my hub. here is what I have done so far:

bill@bill-laptop:~$ sudo apt-get airopeek
E: Invalid operation airopeek
bill@bill-laptop:~$ sudo apt-get install kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libadns1 libgmp3c2 wireshark-common
Suggested packages:
  sox festival gpsd
Recommended packages:
  libadns1-bin wireshark tshark
The following NEW packages will be installed:
  kismet libadns1 libgmp3c2 wireshark-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.6MB of archives.
After unpacking 45.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe wireshark-common 0.99.6rel-3ubuntu0.1 [10.2MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libgmp3c2 2:4.2.1+dfsg-5ubuntu4 [411kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libadns1 1.4-0.1build1 [61.8kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe kismet 2007-01-R1b-1.1 [946kB]
Fetched 11.6MB in 1m37s (119kB/s)                                              
Selecting previously deselected package libgmp3c2.
(Reading database ... 88530 files and directories currently installed.)
Unpacking libgmp3c2 (from .../libgmp3c2_2%3a4.2.1+dfsg-5ubuntu4_amd64.deb) ...
Selecting previously deselected package libadns1.
Unpacking libadns1 (from .../libadns1_1.4-0.1build1_amd64.deb) ...
Selecting previously deselected package wireshark-common.
Unpacking wireshark-common (from .../wireshark-common_0.99.6rel-3ubuntu0.1_amd64.deb) ...
Selecting previously deselected package kismet.
Unpacking kismet (from .../kismet_2007-01-R1b-1.1_amd64.deb) ...
Setting up libgmp3c2 (2:4.2.1+dfsg-5ubuntu4) ...

Setting up libadns1 (1.4-0.1build1) ...

Setting up wireshark-common (0.99.6rel-3ubuntu0.1) ...

Setting up kismet (2007-01-R1b-1.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

 What do I do next?

---

### Post by Siph0n on 2008-01-30
sudo apt-get airopeek wont do anything... you need to do sudo apt-get install airopeek ... that is if airopeek is a valid package... I believe you also have to put your wireless card in monitor mode to use kismet, but im not 100% sure. I do know that the documentation for kismet is pretty good and it gives you detailed instructions how to set it up and run it. Good luck...

---

### Post by doondoon on 2008-01-30
I was going to download airopeek then I remembered kismet was the preferred app for linux users according to the airsnort website. I RTFM I haven't learned how to find what they said. I have to edit the kismet.conf file. How do I find it? I downloaded installed and everything else so far with the shell terminal, and I would like to see it through using the terminal. Any help will get you a TY!!!!!111 ONE!!

---

### Post by Siph0n on 2008-02-02
kismet configuration is loaded to /etc/kismet/

I believe the lines u need to configure are source and suiduser.

---

