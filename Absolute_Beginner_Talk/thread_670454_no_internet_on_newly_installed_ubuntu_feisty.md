---
title: "no internet on newly installed ubuntu feisty"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Desmond Campbell on 2008-01-17
Hi

I've just installed Ubuntu 7.04 (Feisty) alongside the previous OS Windows NT.
Ubuntu seems to work fine except I've no internet access (e.g. firefox won't load up [www.google.com](www.google.com))
Via System, Administration, Network I can see that my Network settings are pretty blank looking.[LIST]
[*]Connections - Wired connection
[*]General - no domain
[*]DNS - there are no DNSs[/LIST]Hosts - are all generic type things (localhost, localnet etc)
I now think during the install I should have imported setting from from the Windows NT administrator, but at the time decided not to.
How can I get my network set up?

regards
Demond Campbell

---

### Post by ijason on 2008-01-17
is this a laptop or a desktop? since you're using 7.04 you'll likely need to get a copy of NdisWrapper. NdisWrapper is the catch-all tool to allow ubuntu to use windows-based drivers, especially for network devices. 

you should be able to find good help by searching google for Ndiswrapper. i had to use it to get my NIC working under 7.04. ubuntu 7.10 seems to have solved the problem though, and i didn't need to load it for it to see my NIC 

good luck!

---

### Post by morgan_greywolf on 2008-01-17
The most common thing to try would be to click on your network connection, click properties and set 'Configuration' to either DHCP or ZeroConf.  DHCP works under most circumstances.  Reboot and you should find everything else (like DNS and domain)  filled out for you.

---

### Post by morgan_greywolf on 2008-01-17
Hi, ijason.  He said right in his post that he has a Wired connection.  That makes ndiswrapper pretty useless for him, as it's generally only needed for wireless connections.  Virtually all wired NICs are based on a small number of different chipsets, all of which have Linux drivers.

---

### Post by Iowan on 2008-01-17
When you say
> **Desmond Campbell said:**
> ... alongside the previous OS Windows NT...

do you mean NT is still available via dual-boot?  If so, you should be able to retrieve your previous settings.

---

### Post by Desmond Campbell on 2008-01-18
> **Iowan said:**
> When you say

do you mean NT is still available via dual-boot?  If so, you should be able to retrieve your previous settings.

Yes, I have a desktop machine wired into the institute's LAN via a 4 core phone cable.
I don't know anything about the type of LAN (probably ethernet). I don't think I need to do I?
And the machine is now dual bootable. I can boot up in NT as well as ubuntu.
I suppose I can try extracting the settings from NT, via Control Panel, Network Connections, although it doesn't look like everything I need is there.

Thanks everybody for your replies, they are much appreciated.

regards
Desmond

---

### Post by seanmiller on 2008-01-18
You're using a router?

If so, the system should just detect it and default to DHCP.... surprised that it hasn't done so.

From shell/terminal, do...

$ ifconfig

...($ is the prompt, so the word "ifconfig") and post what it returns... that'll help...

Also, sometimes simply rebooting the network connecting will do it...

$ sudo ifdown eth0
$ sudo ifup eth0

Sean

---

### Post by Desmond Campbell on 2008-01-20
> **seanmiller said:**
> You're using a router?

Sean

You know what? What I told you last time wasn't quite right.
I have one network socket in the wall, but two computers that need to be connected to the network (One of these computers is the dual boot I've just installed ubuntu on). So to connect both computers to the network, both computers are connected to a little white box with flickering lights on it, and this little white box is connected to the network socket in the wall. Is this white box a router? or could it be some other device, e.g. swtich or hub?

Thanks Sean for you advice. I haven't had a chance to run the commands yet as I've not been in work.

regards
Desmond

---

### Post by philinux on 2008-01-20
Also run

[FONT="Times New Roman"]lspci[/FONT]

this will show the nic model.

---

### Post by Desmond Campbell on 2008-02-01
Hi Anyone who is still listening,

Crisis over
I ran the diagnostic/info programs you suggested above for both the Ubuntu OS and the NT OS.
I sent the results to my system admin person who told me to set it to a static IP address and gave me following to set: the
  IP Address    
  Subnet mask 
  Default gateway 
  DNS Servers: 
(same as my NT OS)

Via Admin, Network Connections, I did that
It didn't work first time. (I think I may have had to click the Activate after inputing the connection settings)
Anyway it works now

thanks all
Desmond

---

