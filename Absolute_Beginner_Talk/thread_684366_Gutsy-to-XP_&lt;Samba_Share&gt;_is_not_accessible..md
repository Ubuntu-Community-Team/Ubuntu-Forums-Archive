---
title: "Gutsy-to-XP: &lt;Samba Share&gt; is not accessible. You might not have permission..."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by VvWolverinevV on 2008-02-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having difficulty accessing Samba shares housed on my Ubuntu 7.10 computer from a Windows XP computer on the same network.  I am hoping that someone can help me find the problem.

From XP, I am able to see Ubuntu via "View workgroup computers," but when I try to open the icon for Ubuntu, I get the error message: ```
\\Tagggggggggg is not accessible. You might not have permission to use this resource. Contact the administrator of this server to find out if you have permissions.

The network path was not found.
```

When I try to access the Ubuntu IP address via Run, I get the error message: ```
\\192.168.1.200

The network path was not found.
```

Notes:
[LIST]
[*]I am able to ping Ubuntu from XP.
[*]I am able to access XP shares from Ubuntu only via Places>Connect to Server...  Places>Network yields an empty folder named "Windows Network," suggesting this confirmed [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386").
[*]My smb.conf file is attached.
[/LIST]

---

### Post by benfindlay on 2008-02-01
Put the following commands into terminal to enable your user account:

```
sudo smbpasswd -L -a your_username
```
You will be prompted for your password, then to set a password and confirm it
```
sudo smbpasswd -L -e your_username
```

Hope this helps!

---

### Post by VvWolverinevV on 2008-02-01
I found the problem.  It's the firewall package Firestarter!  When I stop the firewall, sharing works perfectly in both directions.  I have Firestarter configured to allow all incoming connections from 192.168.1.100/25 though.  What am I missing?

---

### Post by jd65pl on 2008-02-01
Are you sure your network is 192.168.1.100/25?
This gives you:

Subnet mask: 255.255.255.228
Broadcast Address: 192.168.1.127
IP range of: 192.168.1.101 to 192.168.1.126

Is your ip in the range? Can you confirm those net stats? Why not just allow the smb port to all on network? you still have the security of password protection.

J

---

### Post by VvWolverinevV on 2008-02-01
No, my subnet mask is 255.255.255.0 and my broadcast address is 192.168.1.200.  The target IP is 192.168.1.202.  What is the correct way to open ports to a range of IP addresses (say from 192.168.1.100 to 192.168.1.210)?

On the Samba issue, the Firestarter Events tab shows it blocking some dynamic high-number port (like 32985 or 32987) when I try to ping 192.168.1.202 by hostname.  If I open that port to 192.168.1.100/25, everything works fine (until it changes.)  What is that dynamic high-number port, and what is the appropriate rule for opening it to my LAN?

---

### Post by dcstar on 2008-02-02
> **VvWolverinevV said:**
> I found the problem.  It's the firewall package Firestarter!  When I stop the firewall, sharing works perfectly in both directions.  I have Firestarter configured to allow all incoming connections from 192.168.1.100/25 though.  What am I missing?

An understanding of Subnet Masks if your other posts are any indication.

---

### Post by jd65pl on 2008-02-02
> **VvWolverinevV said:**
> If I open that port to 192.168.1.100/25, everything works fine

The 192.168.1.100/25 bit defines a network not the one you have said you are on. Can you post ifconfig so someone can workout what your network is? I'll have a guess at 192.168.1.200/24 from what you've said.

You need to understand network addressing I can explain of post a link if you want or just provide the answer.

J

---

### Post by VvWolverinevV on 2008-02-02
Exactly what part of ifconfig do you need?  I'd rather not post more than is necessary :)  Here's what I think is relevant:
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0

```

Opening to 192.168.1.200/24 seems to be working alright, but I have to allow connections on all ports; it's not enough to only allow connections on the traditional Samba ports.

---

### Post by jd65pl on 2008-02-02
Lol any reason why you're reluctant to post all of ifconfig? What I have told you is correct, you need to allow the smb ports and check the smb server is running. If you get no route to host it suggests it doesn't exist on the network. Trying pinging the ip you believe to be correct for the server if you:

A) get some return
B) are sure you have allowed the correct ports
C) are sure that smbd is running
D) are still unable to connect


Then maybe we need to look at this from a different perspective.

---

### Post by VvWolverinevV on 2008-02-02
Cool.  Like I said, 192.168.1.200/24 seems to be the ticket.  Believe it or not, I read a lot on subnet masks, but I never saw anything that said *my* network address should come before the mask :p

[quote=VvWolverinevV]On the Samba issue, the Firestarter Events tab shows it blocking some dynamic high-number port (like 32985 or 32987) when I try to ping 192.168.1.202 by hostname. If I open that port to [192.168.1.200/24], everything works fine (until it changes.) What is that dynamic high-number port, and what is the appropriate rule for opening it to my LAN?[/quote]
Any ideas on how to open Samba to my LAN without allowing all incoming connections from it?  BTW, in the Events tab Firestarter lists the "service" as sun-rpc portmap.

---

### Post by jd65pl on 2008-02-03
> **VvWolverinevV said:**
> Cool.  Like I said, 192.168.1.200/24 seems to be the ticket.  Believe it or not, I read a lot on subnet masks, but I never saw anything that said *my* network address should come before the mask :p


Any ideas on how to open Samba to my LAN without allowing all incoming connections from it?  BTW, in the Events tab Firestarter lists the "service" as sun-rpc portmap.

I don't think you do understand network addressing, with all due respect. I think you should allow all hosts to connect using the port rather than trying to implement something you don't understand. Either that or learn how network addressing works and you will understand what I meant by my other posts. Is there any particular reason you want to do it this way?

What do you think 192.168.1.200/24 means? Then maybe we can get an understanding of where you are at?

---

### Post by VvWolverinevV on 2008-02-03
192.168.1.200 is the LAN address of my Ubuntu computer.  /24 means the mask (in binary) is twenty-four '1's followed by eight '0's, which is equivalent to 255.255.255.0 (in base 256).  This means that any LAN address which gives 11111111111111111111111111111111 when first ANDed with 192.168.1.200, and then ORed with the inverse of 255.255.255.0, will satisfy the condition 192.168.1.200/24.  This includes 192.168.1.0 through 192.168.1.255. Is this not correct?

---

### Post by jd65pl on 2008-02-03
Ok,

netmask: 255.255.255.0
subnet: 192.168.1.255
ip range: 192.168.1.1 to 192.168.1.254

If you understand addressing you should be able to fix you firewall problem, I'm glad you now understand what I was saying previously.

:)

---

### Post by VvWolverinevV on 2008-02-03
> **VvWolverinevV said:**
> Any ideas on how to open Samba to my LAN without allowing all incoming connections from it?  BTW, in the Events tab Firestarter lists the "service" as sun-rpc portmap.
If you now trust that I understand netmasks, please reconsider my question about the dynamic port.

---

### Post by VvWolverinevV on 2008-02-04
*Bump*

Anyone?

---

### Post by CoolDreamZ on 2008-02-04
> **VvWolverinevV said:**
> I found the problem.  It's the firewall package Firestarter!  When I stop the firewall, sharing works perfectly in both directions.  I have Firestarter configured to allow all incoming connections from 192.168.1.100/25 though.  What am I missing?

I have just spent many hours trying to solve a similar problem with samba and firestarter. Only when I started debugging at the packet level using Wireshark (aka ethereal) did I finally get to solve the problem.

firestarter was blocking broadcast packets on my LAN which prevented netbios name resolution. Everything worked fine with the firewall off! To fix the problem:

Start Firestarter
Edit->Preferences
Advanced Options
Ensure "Block broadcasts from external network" and "Block broadcasts from internal network" are both unchecked
Stop/Start the Firewall

For some reason firestarter thinks my LAN is an "external network" - I haven't figured this part out yet!

Hope this helps

---

### Post by christhegoth on 2008-02-05
I have the same problem, and same error message.  Firestarter is now adjusted so I'll keep trying.

---

### Post by VvWolverinevV on 2008-02-08
CoolDreamZ, I unchecked "Block broadcasts from external network", but I am still not able to ping XP by hostname.  The Blocked Connections tab in Firestarter shows

Port: 32956
Protocol:UDP
Service: Unknown

---

### Post by dca on 2008-02-08
Wait a minute, my head just spun from the last two pages.  You're trying to get Samba working on the Ubuntu box and access from an XP machine.  The share & user have been enabled w/ the smbpasswd -a & then -e commands but Firestarter appears to be the issue?  Do I have this right?
 
The only thing I can think of is in Firestarter, click on the policy tab, and from the Editing drop-down menu select 'Inbound Traffic Policy'.  Click 'Add Rule' button and the next window use the 'name' drop-down menu to select SMB,Samba which should automatically populate the policy area w/ ports 137-139, 445...  Then restart the firewall....

---

### Post by VvWolverinevV on 2008-02-08
This is the issue, dca.  137-139, 445 is apparently not enough.  There is additionally a dynamic port.  In my last post, that port was 32956, but it changes periodically.

---

### Post by tsnj on 2008-02-27
> **VvWolverinevV said:**
> This is the issue, dca.  137-139, 445 is apparently not enough.  There is additionally a dynamic port.  In my last post, that port was 32956, but it changes periodically.

Those upper ports sounds like one of the peer applications, i.e. bittorrent, azureus, etc.  You can look through the help files of those application for how to set up a range of open ports.  I recall going through that some time ago, but it may have had more to do with isp's rather than firestarter.  Still, searching for that kind of info will probably turn up your answer.

---

### Post by VvWolverinevV on 2008-02-27
Nope, the port I'm talking about concerns:
1) pinging by hostname
2) browsing the Windows network in Nautilus

It has nothing to do with p2p.

---

### Post by CoolDreamZ on 2008-02-29
> **VvWolverinevV said:**
> CoolDreamZ, I unchecked "Block broadcasts from external network", but I am still not able to ping XP by hostname.  The Blocked Connections tab in Firestarter shows

Port: 32956
Protocol:UDP
Service: Unknown

I have not been able to use ping with a hostname etiher. I think for this to work you would also need to implement DNS (or possibly a WINS server?). This does not affect using hostnames with samba as it can resolve them using the NETBIOS protocol.

---

