---
title: "Firestarter and VPN"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by PeaceMessenger on 2005-10-15
I have been struggling to get my VPN working, but finally with success. I'm using PPTP-linux 1.5.0-5ubuntu and pptpconfig which I learned how to install from [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)  

 It works only if I disable the firewall in Firestarter.   Firestarter has some things on it's website [http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php) about a workaround for a vpn.  The work around they posted for connecting to a Microsoft VPN is :
------------------------------------------------------------
How to use the VPN workarounds in Firestarter 1.0

Copy the lines specific to your VPN solution listed below, and paste them into the /etc/firestarter/user-pre file on the firewall host. Restarting the firewall, for example by executing "/etc/firestarter/firewall.sh start", commits the new settings.
Microsoft VPN clients

The widely used VPN solution for Microsoft Windows machines is based on the PPTP protocol. The following lines allow PPTP clients on the Firestarter administered local network to connect to remote servers:

# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

----------------------------------------------------------------------------------------
OK, The first challenge I had was to open the /etc/firestarter/user-pre  file for editing.  I found it in the file directory, but it won't open.  Aahh, I think I found why.  It is owned by root.  So I used the command under Applications-> System Tools->Run as different user and I typed *gedit *to open the text editor as root.  Then I could open the user-pre file, which was absolutely empty.  I cut and pasted the above lines into it, saved it, and then tried to restart the firewall.   I couldn't figure out how to execute */etc/firestarter/firewall.sh start* and so I decided to
just reboot the machine.  That should restart the firewall, right?

Well, still no luck.  I still have to turn off the firewall to make the vpn work.  I decided to add a policy to firestarter.  I added an inbound traffic policy to allow connections from the host, and entered in our VPN servers IP address.  Hey, guess what... the vpn could connect-  but still nothing works through it.  It connects but then I can't even get to google.  I turn off the firewall and everything works fine.

Any ideas what I am doing wrong?  I would like to use the VPN and the Firewall both.

---

### Post by Nikola Kasabov on 2005-10-22
Absolutely same here.

And this happes when for internal (LAN) network is selected eth0 and external (internet) eth0.
If internal (LAN) is selected eth0 and external (internet) is ppp0 then the pptp connection can not be started.

---

### Post by PeaceMessenger on 2005-10-25
I installed Kubuntu over Ubuntu and then switched to using Guarddog instead of Firestarter.   The VPN works now.

I did find that if I close the pptpconfig window while the VPN is running, it completely messes up my internet connection and at first I would have to reboot to get it to work, but then a friend shared with me these commands.

sudo ifdown eth0
sudo ifup eth0

Then everything works again.  Hopefully in future versions of Ubuntu vpn's can be run without having to do tweaky stuff.

---

### Post by reuben on 2005-11-28
Echoing the above; I installed GuardDog instead of Firestarter; opened VPN & PPTP for the internet zone. Everything works now.

---

### Post by jmooney on 2005-11-28
[QUOTE=PeaceMessenger]I have been struggling to get my VPN working, but finally with success. I'm using PPTP-linux 1.5.0-5ubuntu and pptpconfig which I learned how to install from [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)  

 It works only if I disable the firewall in Firestarter.   Firestarter has some things on it's website [http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php) about a workaround for a vpn.  The work around they posted for connecting to a Microsoft VPN is :
------------------------------------------------------------
How to use the VPN workarounds in Firestarter 1.0

Copy the lines specific to your VPN solution listed below, and paste them into the /etc/firestarter/user-pre file on the firewall host. Restarting the firewall, for example by executing "/etc/firestarter/firewall.sh start", commits the new settings.
Microsoft VPN clients

The widely used VPN solution for Microsoft Windows machines is based on the PPTP protocol. The following lines allow PPTP clients on the Firestarter administered local network to connect to remote servers:

# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

----------------------------------------------------------------------------------------
OK, The first challenge I had was to open the /etc/firestarter/user-pre  file for editing.  I found it in the file directory, but it won't open.  Aahh, I think I found why.  It is owned by root.  So I used the command under Applications-> System Tools->Run as different user and I typed *gedit *to open the text editor as root.  Then I could open the user-pre file, which was absolutely empty.  I cut and pasted the above lines into it, saved it, and then tried to restart the firewall.   I couldn't figure out how to execute */etc/firestarter/firewall.sh start* and so I decided to
just reboot the machine.  That should restart the firewall, right?

Well, still no luck.  I still have to turn off the firewall to make the vpn work.  I decided to add a policy to firestarter.  I added an inbound traffic policy to allow connections from the host, and entered in our VPN servers IP address.  Hey, guess what... the vpn could connect-  but still nothing works through it.  It connects but then I can't even get to google.  I turn off the firewall and everything works fine.

Any ideas what I am doing wrong?  I would like to use the VPN and the Firewall both.[/QUOTE]


Ok to run the Firestarter shell command type:

sudo sh etc/firestarter/firewall.sh start

It will ask for your password the it give you a message confirming that the firewall started.  Now, maybe you can help me.

I also have Firestarter.  I also added the recommended edits to user-pre and had to set a policy to allow connections for my work VPN server address, and I'm having the same problem as far as getting an active connection but not being able to do anything with it.

I try pinging the server from the debug window and ping fails.  However, when I stop the firewall and try again, ping works just fine.

So, the firewall is off and ping is working, how do I browse files on the other side of the VPN tunnel?  Or better yet, how do *you* browse files on the VPN network? 

Thanks,

Joe

---

### Post by PeaceMessenger on 2005-11-29
Joe,

I switched to using Guarddog for the firewall and that made it easier and everything worked.  I suggest trying that.

I use our vpn only for email and can browse a private company webpage our tech people have put up- so I just use an internet browser and type in the ip address of the webpage server.   That's really all I know how to do.

---

### Post by ngms27 on 2005-11-29
If you are trying to access Windows resources then I think you will need Samba installed on your machine. However I have never connected to a VPN using Linux! 

e.g. if you have a share on server1 called sharedfiles then you would have to access \\server1\sharedfiles. More than likely you will then be prompted for your credentials.

I have done many Windows VPNs using Cisco Pix firewalls. The browsing service on Windows NT networks is not routable so Browsing generally requires tweaks and even then can be flaky hence my suggestion to connect to resources. 

On Active Directory domains you will need your DNS using the AD DNS as default. Some VPN clients such as Cisco's can force this down to the machine.

Definately one to Lab I think!

JonnyT

---

