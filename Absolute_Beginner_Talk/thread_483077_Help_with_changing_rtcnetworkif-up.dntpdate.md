---
title: "Help with changing /rtc/network/if-up.d/ntpdate"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by shoryuken on 2007-06-24
Hello,

Since this is my first post allow me to begin by thanking all those involved in this forum. It has been a great tool. I have finally been able to dedicate a laptop to Ubuntu and thanks to this forum I've been able to get around a few problems that I have had through the set-up process. 

I sincerely apologize if this is posted in the wrong place.

Anyway, to get to the topic at hand. This is one problem that I have not been able to find a solution to but I have an idea as what I want to do but just don't know how to do it yet.

The problem is that I have noticed that ntpdate tries to connect to an ntp server right after I log into the desktop. since at that point in time my wireless network is not logged in yet ntpdate hangs the system as it waits for a response. Here is an example of the system log:

> 

Jun 24 11:34:03 BlueGiant avahi-daemon[4630]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun 24 11:34:03 BlueGiant dhclient: No working leases in persistent database - sleeping.
Jun 24 11:34:08 BlueGiant avahi-autoipd(eth1)[5308]: Callout BIND, address 169.254.6.123 on interface eth1
Jun 24 11:34:08 BlueGiant avahi-daemon[4630]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.6.123.
Jun 24 11:34:08 BlueGiant avahi-daemon[4630]: New relevant interface eth1.IPv4 for mDNS.
Jun 24 11:34:08 BlueGiant avahi-daemon[4630]: Registering new address record for 169.254.6.123 on eth1.IPv4.
Jun 24 11:34:12 BlueGiant avahi-autoipd(eth1)[5308]: Successfully claimed IP address 169.254.6.123
[B]Jun 24 11:34:12 BlueGiant avahi-autoipd(eth1)[5308]: fopen() failed: Permission denied
Jun 24 11:34:56 BlueGiant ntpdate[5375]: can't find host ntp.ubuntu.com 
Jun 24 11:34:56 BlueGiant ntpdate[5375]: no servers can be used, exiting
Jun 24 11:35:38 BlueGiant NetworkManager: <information>^IUpdating allowed wireless network lists. 
[/B]Jun 24 11:35:38 BlueGiant NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
Jun 24 11:35:38 BlueGiant dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun 24 11:35:38 BlueGiant NetworkManager: <information>^IWill activate connection 'eth1/myHome'. 


I've highlighted where the hang occurs. Now everytime ntpdate can not connect to the server the system just hangs. I've looked in /rtc/network/if-up.d/ntpdate and although I've never written a shell script I kind of understand what the script does and how things are passed to other scripts depending on if $METHOD is **loopback** or **static**. 

I'm thinking that there is away around this.:-k What if the script checked to see if the internet connection is really up by sending a packet (perhaps through ping) to a fix ip address and if there isn't an immediate response, then let the rest of the process go through. Any suggestions as how this could be incorporated into the script?

Thanks in advance for any suggestions.

---

