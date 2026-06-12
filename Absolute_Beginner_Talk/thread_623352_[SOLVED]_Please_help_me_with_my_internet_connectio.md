---
title: "[SOLVED] Please help me with my internet connection and installs please"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Damien Kane on 2007-11-25
Hi there - how are you!

I'm another sick-of-Windaz user who wants to use an alternative, and have a dual boot Windows-Ubuntu configuration. The config isn't a problem, but I have issues using internet and installing. My hardware configuration is, if you need to know it:

Basics: MSI Pm8M-V (P4M800 + VT8237 chipset) motherboard running 3.2 socket 478 Prescott, 2GB RAM, 2xDVDRW, Radeon9600. Motherboard includes ethernet on an external D-Link DSL-502T router (not wireless) broadband.

I've only been using Ubuntu for a day and have to reboot to use the internet, so I apologise if I get some of the following names wrong, however:

After turning on the modem, the network box in Ubuntu the top right appears to be connected after a couple of minutes - same as Windaz, but I can't surfcheck POP mail, etc. Using the "Terminal", I pinged a few websites and had returned bytes. I tried to follow the help system in Ubuntu but still nothing. I have a direct connection. I checked the hardware manager, and there appears to be an ethernet adapter installed. There's somewhere in the Administration section with network tools, and I pinged some other sites and it was connected.

When I right click on the network box and go to connection information, it also seems to be connected.

I had also downloaded a firewall (Guard Dog) to install before I went on the net, but I don't know how to install it. I followed the instructions and had to use the Terminal, but it lost me. So, I used the add program feature. It seemed to download a list of applications and I chose to download Firestarter, but it didn't download.

So, my questions are: (a) how do I get my internet connection working properly, and (b) how on earth do I install things I download?

I'm completely new to Linux. I believe it'll be the future of operating systems, but it's got a way to go, and I want to get used to it so I can help people, but I need help in getting there.

I appreciate the Linux community coming up with Ubuntu. Thank you.

---

### Post by Partyboi2 on 2007-11-25
Could your problem be with your routers firewall?
I once had a problem, where I could not retrieve my email, but that was another distro, but I worked it out it was the routers firewall.
Don't know if thats your problem or not.
Is this only when you are trying to use a web browser to surf, email etc?

---

### Post by Damien Kane on 2007-11-25
It's a standard ADSL router ([http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48](http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=1&Sub2=2&PID=48)). I can ping, but I can get nothing else including ftp, http and POP. I tried all the help info I can find. Leads etc are fine. It's probably something silly.

---

### Post by rexxxlo on 2007-11-25
you dont generally download programs to install like m$ you use the repository  or synaptic try to click>applications>add remove that is usually what you use to install programs 

almost everything i have needed is in there its so easy give it a try 

a cant help with the networking problem although the firewall isn't necessary as i understand and i bet you can get by without  but that is just my opinion

---

### Post by jcsteele on 2007-11-25
Can you open up a terminal window (Applications -> Accessories -> Terminal) and type in the following:

     lspci 

    ifconfig

type each command in seperately and then copy/paste/post us the results of each command.  This will better allow us to help you.

//jcs

---

### Post by Damien Kane on 2007-11-25
Hope all this makes sense!

Can you open up a terminal window (Applications -> Accessories -> Terminal) and type in the following:

lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:D3:38:2A:EA  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:d3ff:fe38:2aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3846 (3.7 KB)  TX bytes:6675 (6.5 KB)
          Interrupt:18 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

type each command in seperately and then copy/paste/post us the results of each command. This will better allow us to help you.

//jcs
bash: //jcs: No such file or directory

---

### Post by jcsteele on 2007-11-25
Yes, it does make sense :)

It lets us know that you indeed have a functioning network controller, with an IP Address of 10.1.1.2  I am going to go out on a limb and say that your router probably has an IP address of 10.1.1.1 - you should be able to run a "ping 10.1.1.1" and get a good response.  (this is all assuming that your router has a dhcp server installed and it gave you your 10.1.1.2 lease)

Does your adsl account require you to login?  If so, have you set this up in the router?  Is your router plugged into the adsl modem, or is the router connected directly to your phone line?

Ex.

COMPUTER ------ ROUTER ------ ADSL MODEM ----- PHONE LINE
                            OR
COMPUTER ------- ADSL MODEM ----- PHONE LINE

//jcs

---

### Post by Damien Kane on 2007-11-25
The second one: COMPUTER ------- ADSL MODEM ----- PHONE LINE

When I first got the internet a couple of years ago, I had to enter a username and password (in Windows). I had to re-install recently but it never asked me for it. After installing Ubuntu, it never asked.

You're right also on the IP 10.1.1.1. If I enter this in a browser (ie, Firefox), it comes up with lots of options for the router, but there's no help for Linux. My username and password are in there. Hm - maybe I should do the same under Linux. Will try that at one point.

Any ideas!

thanks for your help, by the way.

---

### Post by stevemu on 2007-11-25
Is your modem/router showing a green light for the ADSL Link and the Ethernet Link?

Please confirm you are connecting to the modem/router via ethernet and not via USB

---

### Post by Damien Kane on 2007-11-25
I'm connecting through ethernet, and just verified the username, password and router 10.1.1.1 and all upstream and downstream tests passed. Lights are all OK. Ping still works but everything else doesn't. I also tried USB but everything is exactly the same.

---

### Post by stevemu on 2007-11-25
Have you installed Firestarter?

It should be under Applications->Internet.  Or open a terminal and type 'sudo firestarter'.

Open it up and check your policy for outbound traffic.  It should be set to "Permissive".  I just set mine to 'Restrictive" and got the same symptoms you have.  i.e. I could ping but could not open a browser page,.

I'm sure there is another way to check this outside of Firestarter but I don't know how.

---

### Post by Damien Kane on 2007-11-25
I just had a thought: when installing, Ubuntu imports settings from Windows. I had Windows configured (but turned off) through The Tor Project through proxy 127.0.0.1:8118. Even though it was disabled in Windows, maybe Ubuntu used it as default. Perhaps there's a global proxy setting for Ubuntu where I can use direct connection instead of proxy, instead of pointing the individual applications. Just a thought, perhaps the only one this week, but it's a thought!!

---

### Post by Damien Kane on 2007-11-25
OK - here's an update on the problem!!

- Found the global proxy setting and it's on direct connect;
- Firefox is on direct connect;
- Firestarter is not installed - Ubuntu can't download anything to install;
- All diag tests support up and downstream tests are fine;
- The only thing that works is ping!

Stumped. Sorry everybody.

---

### Post by jcsteele on 2007-11-26
Enter "cat /etc/resolv.conf" in the terminal and post the output below....

Something is amiss with your connection, but I am running out of answers.  Assuming your router is actually a true router, you should not have to provide any kind of connection information to it from the ubuntu machine...however, it is a stand alone modem, this might be the case and you will need to use something like [http://ubudsl.ubuntu.pl/index_en.html](http://ubudsl.ubuntu.pl/index_en.html) to setup the connection.  Once I get the output above, it should be clear if your router is passing the appropriate DNS information onto the ubuntu machine or not....which is just one more piece of the puzzle.

//jcs

---

### Post by polhen on 2007-11-26
hi !

i just installed fedora 7 on my system...but i cant access internet ...network info says my ip is 169.254.x.x  this wrong, because i need 192.168.x.x network ip.
could you please ...tel me  how do i access network configuration manager, so i can change network settings...to proper one....

help will be appreciated

regards
pol

---

### Post by Damien Kane on 2007-11-26
Hi all -

sorry I've been away for a while. I called up a number of people and a friend called me back and explained that the firmware for the DSL-502T router has to be installed. I didn't have the most recent version - must've missed that one in my driver updates.

He had advised to download the recovery package because these modems are apparently prone to such things when updating firmware - very useful, because it did crash, and took a while to get back online.

Anyhow, updating to the most recent firmware allowed me to connect to the internet. I hope other people get this post if they have the same issue.

Thanks so much for all your advice. You've all been a great help. I'm writing this in the Ubuntu system, and it's great. Lots of things to learn. Thank you so much. The only thing I need now is a firewall that's about as good or better than Comodo for Windaz ([www.comodo.com](www.comodo.com)) for outgoing connections!

---

