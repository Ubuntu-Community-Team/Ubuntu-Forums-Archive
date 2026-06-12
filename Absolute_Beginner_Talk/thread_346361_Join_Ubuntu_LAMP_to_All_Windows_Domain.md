---
title: "Join Ubuntu LAMP to All Windows Domain"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by mahalie on 2007-01-25
Hello, 

I'm sure my question will reveal what a total newb I am...I installed Ubuntu server (LAMP) and it's up, updated and running fine (as far as I can tell). I want to add it to our all windows corporate domain (we use AD), or rather want my sysadmin to add it. 

Is there anything special I need to do add it?  I'm just read '[Network Configuration]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html")' in the server guide and I don't really know networking but it seems it should just work on my end, although, my sysadmin is going to give me a static IP address.

Can someone provide an example of what I would enter, say in the resolv.conf file? Do I need our DHCP server's IP address or just the domain name (corp.domain.com)?

My goal here is to add the box to our network so I'll be able to browse to my ubuntu servers pages via [http://ubuntuservername](http://ubuntuservername)

---

### Post by mahalie on 2007-01-25
I really don't know what I'm doing when it comes to tcp/ip, dns, basic networking, please help! I've documented everything I've tried so far using the [Server guide]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html") and [a tutorial on Howto Forge]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3").

**My sysadmin sent me the following info:**
Static IP Address:  10.0.0.75
Subnet Mask: 255.255.252.0
Gateway: 10.0.0.1
DNS Server: 10.0.0.53

I changed *interfaces *to
[FONT="Courier New"]iface eth0 inet static
	address 10.0.0.75
	netmask 255.255.252.0
	gateway 10.0.0.53[/FONT]

[FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT]


[FONT="Courier New"]ping serverx[/FONT]
64 bytes from serverx.corp.domain.com (127.0.1.1)
56 pakcets transmitted, 56 received, 0% packet loss

on my windows desktop from cmd [ping ubuntu - serverx]
[B][FONT="Fixedsys"]ping serverx
Ping request could not find host serverx. Please check the name and try again.[/FONT][/B]

[FONT="Fixedsys"]ping 10.0.0.75 
success (0% loss)[/FONT]

[serverA.corp.domain.com] - my windows test server 
[FONT="Fixedsys"]ping serverA
success (0% loss)[/FONT]

changed *interfaces* back to 
[FONT="Courier New"]iface eth0 inet dhcp

/etc/init.d/networking restart[/FONT]

again from cmd on my windows desktop
[FONT="Fixedsys"]ping 10.0.0.75 
request timed out. (100% loss)[/FONT]

on my ubuntu server (same as before)
X bytes from serverx.corp.mithun.com (127.0.1.1)
Y pakcets transmitted, Y received, 0% packet loss 

Switched *interfaces *back to:
[FONT="Courier New"]iface eth0 inet static
	address 10.0.0.75
	netmask 255.255.252.0
	gateway 10.0.0.53[/FONT]

Also, changed hosts (*/etc/hosts*)

from 
[FONT="Courier New"]
127.0.0.1       localhost.localdomain localhost
127.0.0.1 	serverx.corp.domain.com     serverx[/FONT]

to
[FONT="Courier New"]
127.0.0.1       localhost.localdomain localhost
10.0.0.75 	serverx.corp.domain.com     serverx[/FONT]

but hostname returns serverx and hostname -f returns serverx.corp.domain.com, even after reboot

they both should return serverx.corp.domain.com, right?
pinging (from my windows desktop within the network) the ip address works, but pinging the server name (serverx) returns ping request could not find host serverx.

what am i missing here? please help!

---

### Post by Daremo on 2007-01-25
if you can ping the IP addess from the Windows machine then the Unbuntu box is working. Your sys admin will need to add a DNS entry for the Ubuntu box in the Windows domain. This "translates" the numerical IP address into the "name" of the Ubuntu box and after the DNS entry is complete it should work. If not you'll neeed to discuss this with your sys admin further...

---

### Post by mahalie on 2007-01-25
> **Daremo said:**
> if you can ping the IP addess from the Windows machine then the Unbuntu box is working. Your sys admin will need to add a DNS entry for the Ubuntu box in the Windows domain. This "translates" the numerical IP address into the "name" of the Ubuntu box and after the DNS entry is complete it should work. If not you'll neeed to discuss this with your sys admin further...

He says to add a box to our domain he logs onto the new box to join, because you need admin rights to do it. He's never added a linux box to the network before. I googled it and saw a lot of mentions of SAMBA. Is this something I should look into?

---

### Post by Daremo on 2007-01-26
> **mahalie said:**
> He says to add a box to our domain he logs onto the new box to join, because you need admin rights to do it. He's never added a linux box to the network before. I googled it and saw a lot of mentions of SAMBA. Is this something I should look into?

Samba is for file sharing between linux and windows. If this is also what you want to do, then yes. If you're just interested in using a "name" instead of having to type an IP address to connect to the linux box then a DNS entry should be all that is needed.

there are ways to have a linux box join an Active Directory domain and allow for users to authenticate (logon) with AD credentials (WinBIND), however I have not tried this with Ubuntu. I have done successfully several times with Suse and it works ok. The basic setup will not apply any Group Policy Objects though to linux.

one catch I encountered a while ago was with one organization that used spaces in the logon name for the users. This caused a lot of problems with AD authentication in linux and even with other linux apps that tried authenticating with Windows Server's LDAP components, so from what i have seen using spaces in logon names is not a good idea.

---

### Post by mahalie on 2007-01-26
Daremo, thanks a bunch!

It did finally work. He added the name on the Domain name server and it just took a while to propagate. I don't think we need to file share at this point, but I would like to work with Active Directory.  I found this forum post: [Howto: Ubuntu server as an Active Directory member server]("http://ubuntuforums.org/showthread.php?t=280702") which seems to be exactly what I need.

---

