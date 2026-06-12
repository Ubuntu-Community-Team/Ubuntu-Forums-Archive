---
title: "Help please: PPP Connection Woes"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Noir on 2006-05-14
HI there, I just started Linux / Ubuntu, and I finally set up my PPP profile to access the internet using my local ISP connection that requires username and password.  Thanks to the forum member who pointed me to pppoeconf!

But what I am seeing that everytime I "pon dsl-provider", the ppp0 interface (not sure what the correct terminology is) will show up and I will get access to the internet.  However, after a while (usually in the order of 5-10 minutes), the connection will stop working and I will have to restart the ppp0 interface by issuing a "poff dsl-provider" followed by another "pon dsl-provider" command.  

This is extremely annoying and I am sure this is not the expected behavior.  I am wondering if anyone can point me to some help so that I can heve the connection be "sticky".  I have another computer at home accessing the same wireless access point sharing the same ISP connection and that box is accessing the internet just fine.

A couple of really weird things I noticed:

- The IP address of the ppp0 interface is very strange: 218.1.85.1.  This is radically different from the IP that was obtained on the other PC.  How do I look at the DHCP and other settings for the ppp0 interface?

- When I try to configure the ppp0 interface under the GNOME GUI, it always shows the ppp0 interface as a Modem.  When I look at the configuration options it's all about dial-up numbers and other options unrelated to PPP.  Is there a way to fix this and get to the real configuration options?

Any help will be greatly appreciated!

- Noir / K

---

### Post by ProjectGod on 2006-05-14
i'm confused. ppp or pppoe? dial up or broadband?

can you clarify the setup you have. whether its an ADSL or cable...and more details on the hardware used. cabling if any or is it all WIFI? the modem / router vendor / model etc.

---

### Post by Noir on 2006-05-14
Hi ProjectGod, this is actually a continuation of a different thread from before.  Here is the summary of the setup.

I have a cheap Linksys wireless switch that I use to connect to the ISP Broadband.  The ISP connection is ADSL and requires a separate username and password in order to connect to the ISP's network.  Since my switch is really brain-dead, it is not able to auto-connect to the ISP to establish an 'always-on' internect connection.

So to address this, a forum member told me to run "sudo pppoeconf" and follow the setup instructions to establish the username and password for my PPPOE connection.  This successfully gets me on the internet, however, the connection will have problems after about 5-10 minutes (seems to be DNS problems) and I will have to bounce my ppp0 interface in order to restore my connectivity.  On the other hand, my other Laptop connected to the same wireless switch is accessing the internet just fine.

My Ubuntu 5.10 installation is on an archaic ThinkPad with a Linksys DWL-G630 PCMCIA wireless card.  I've installed clean and my ThinkPad has no other OS installed.  My wireless switch is also a Linksys, model BEFW11S4.

I hope this can help you help me...

Cheers,
- K.

---

### Post by ProjectGod on 2006-05-14
oh... wireless switch. you mean a routing device that has wireless capabilities with the phone line directly connected into it? if so then. it's quite simple... 

firstly most ADSL routing devices, wifi or ethernet (cable) based SHOULD and CAN basically act as the DEFAULT GATEWAY. meaning... if you have the kind of setup you have described, you have no need to use the terminal to enable connectivity to the internet via the router. i.e. using "pon dsl-provider" etc etc. after saying this... please answer the following qs to narrow the problem down to its source.

1. is the wireless switch (router ) DHCP enabled?
2. the other machine... is it a windows? or a ubuntu? if windows. go to command prompt. (start run "cmd") and check IP addr allocation with the command "ipconfig /all". it should tell you if it's dhcp enabled etc and the current address leased out. if ubuntu. use "ifconfig" at terminal to see if its dhcp enabled. or using static ips.
3. when you have brief connectivity to the internet with the troublesome machine, can you also access the other laptop's resources? or at least can you PING the other machine? (terminal... ping x.x.x.x). try this when your internet connectivity is broken also.

basically if the router is functioning correctly you'll have a little workgroup like connectivity between the two machines. now try:

4. if answer to q1, is yes. the router is DHCP enabled. then check your ubu machine. make sure the WIFI network adapter is DHCP enabled. do this under "network settings... GUI utility... select the network adapter (wifi) and make it DHCP enabled... 

in other words... make sure all devices / hosts are using the same addressing scheme. if router is DHCP enabled. then the two hosts should be DHCP enabled. otherwise if the router not DHCP enalbed then static addresses must be allocated to the host machines. you must use the same addressing scheme / subnet mask / default gateway address (router ip paddress).

5. now on the ubu machine... under "network settings"... go to the DNS tab. insert your ISP's DNS server's address...  if you don't know ring them up or go to the other machine log into the router and check the settings for ISP's DNS server...

6. try rebooting the ubu machine... then log in and open up firefox web browser.

please all answer these questions and we'll be well on our way to unbroken internet connectivity!

hope this helps.

--------------------------------------------------------------------------

---

### Post by Noir on 2006-05-15
Thanks for the reply again, ProjectGod!

So first let me answer your questions:

1. The Wireless router is DHCP-enabled.
2. The other laptop is Windows XP.  The TCPIP settings on the Windows box is DHCP enabled, and all IP addresses are selected to be automatically obtained.
3. I know the router is functioning properly, because the router's DHCP table shows the assigned IP addresses for both my Windows and Ubuntu boxes.

So before I head down to more answers, I think I found out a behavior that caused the problems - but I don't know what caused it.  But before I go there, I want to explain why I need to do the "sudo pon dsl-provider" step.

My ADSL Broadband provider requires a separate username and password to allow my machines to connect to their broadband network.  I am not able to connect to the ISP without this step, and they way I was told to do this is to set up a PPPOE "interface" using "sudo pppoeconf".  My machine was able to access the broadband network after this step.  If I don't take this step, I get zero connectivity and there will be a "Do not enter" sign over the "Network Connection" icon.  Some routers can be configured to automatically logon to the broadband provider to achieve an "always on" connection from the perspective of the client PCs, but unfortunately, mine does not.

Now with that out of the way, what I am seeing is this:

1. At some point in time I configured a PPPOE inteface using pppoeconf, and set up the username, password and other connectivity options for my broadband provider.  I set the connect option to manual, instead of autoconnect on boot.

2. I manually start the PPPOE using "sudo pon dsl-provider".  I check ifconfig and the ppp0 interface is started.  The dynamically assigned IP looks good, although the P-t-P IP is strange (24.24.24.24).

3. I open the System->Administration->Networking and check the DNS server IPS, and there are 2 of them, and they match the DNS server IPs on my Windows box.  This is good.

3. I start the FireFox browser and I get connectivity.  I can browse the web with no problems for about 5 minutes, after which, the browser will get stuck on the DNS, and eventually report that the domain name could not be found.

4. Now, after I lose DNS functionality, I go back and open System->Adminiation->Networking and check the DNS again, and this time, the DNS addresses are gone, and I get 192.168.1.1 instead!  As you might recognize, this is the local IP address for my router's admin configuration page.  

5. If manually change this back to the actual DNS servers, I actually get connectivity again, for about 5 mins, where the DNS server IPs will be replaced again, with 192.168.1.1.  The same happens if I bounce the ppp0 interface by a sequence of "poff" followed by "pon".

So I think this is the problem, but I have no idea why this is happening.  My best guess is that there is a daemon somewhere that is trying to access my router configuration periodically.  But even that, it shouldnot be messing with my DNS settings.  One thing I did was that I actually set an admin password for my router configuration so if there was a daemon, it would not be able get through to my router configuration.

So I hope someone will be able to recognize this problem and let me know what is happening, and better yet, help my get back online again.   :-)

Many thanks in advance!
- Noir / K.

---

### Post by ProjectGod on 2006-05-17
i'm currently at work, and am using a windows machine. so i cannot simulate any ubuntu commands. :(  right at this moment. 

after you loose connectivity can ping lets say... [www.google.com](www.google.com) ? if you can ping this url then see if you can use the IP address of google to connect to it instead of the url. 

one more thing does the router have capabilities to store in its memory the ISPs DNS server address? do you have to enter your username / password combination from your xp machine everytime you want to connect!? :eek: 

what i think that's happening... is that the DHCP lease period on your router is set too short a period. that... and whenever your ubuntu machine tries to get new IP settings from the dhcp it grabs the "default" dns server address in this case the router itself.... so one thing to check is to connect to the router from the xp machine and try to configure the DHCP configuration settings... the DNS server address it leases out should be the ISPs dns server.

so the solution may very well be. to disable DHCP on the router. set static ips on the router and all machines and manually insert the ISPs DNS server address...

hope this works out.

---

### Post by Noir on 2006-05-17
Hi ProjectGod, thanks for your continuous support.  I really appreciate it.

I cross-posted this thread to the Networking Forum, and I got a few replies that helped me solve the problems.  I would like to share this [thread ]("http://www.ubuntuforums.org/showthread.php?t=177598")with you and other readers who are curious as to how this problem was solved.

Once again, I want to thank ProjectGod for sharing his advice and helping all the way.  I learned a lot from this troubleshooting incident and I hope to continue to learn from ProjectGod and others alike.

Thanks,
- Noir / K.

---

