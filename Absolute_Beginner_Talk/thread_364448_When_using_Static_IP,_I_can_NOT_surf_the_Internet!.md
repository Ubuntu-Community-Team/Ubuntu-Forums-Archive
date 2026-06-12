---
title: "When using Static IP, I can NOT surf the Internet!"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-18
Hello!

_I have the following question_:

I have the following configuration:

1. One PC with [color=red]WinXP Pro[/color]
2. One PC with [color=red]WinXP Pro[/color]
3. One [color=red]Router[/color] that connects these 2 PCs
4. Setup the Network & these PCs can see each other

_The problem_:
When these PCs are both assigned [color=blue]Dynamic IPs[/color] -> Network works fine & Internet surf works!
When these PCs are both assigned [color=blue]Static IPs[/color] ----> Network works fine but Internet surf does **NOT** work for any of them...

Any ideas how to fix this?
Thanks.

P.S.1> When using [color=red]Ubuntu[/color] PCs, no matter whether I assing Static IPs or Dynamic IPs, both of the PCs can access the Internet!
Why does this happen _only_ when using Windows OS?

P.S.2> As soon as I get this done, I will try to Network an Ubuntu PC with a WinXP PC (through "samba"). But one thing at a time...

---

### Post by bulldog on 2007-02-18
Try a windows forum :)

---

### Post by jonathan.lees on 2007-02-18
With a DHCP address, open a command prompt and type ipconfig /all and copy what is displayed. Then set your static IP address and do the same and paste both the results here.

---

### Post by steve.horsley on 2007-02-18
I do know that DHCP can issue more information than just an IP address ans subnet mask to use. It can also issue the IP address of the router (default gateway) to the internet, and the IP addresses of one or more DNS servers for doing name->IP address lookups.

In windows, use the command **ipconfig /all** (or perhaps it's -all instead) to see what is set. My guess is that the default router or the DNS server is missing from the static configuration. I suggest you copy the settings reported by the DHCP configuration when configuring the static parameters.

---

### Post by dvarsam on 2007-02-18
sorry, just a typo here...

---

### Post by dvarsam on 2007-02-18
[QUOTE=steve.horsley]I do know that DHCP can issue more information than just an IP address ans subnet mask to use. It can also issue the IP address of the router (default gateway) to the internet, and the IP addresses of one or more DNS servers for doing name->IP address lookups.

In windows, use the command **ipconfig /all** (or perhaps it's -all instead) to see what is set. My guess is that the default router or the DNS server is missing from the static configuration. I suggest you copy the settings reported by the DHCP configuration when configuring the static parameters.[/QUOTE]

The default Gateway is fine!
It is 192.168.1.2
I have checked this on the Router's settings - besides all the PCs connect to the NET when assigned a Dynamic IP...

Sorry, but why does DNS need to be set up/assigned?
I thought that the Router saves all the ISP's DNS info...
Do I need to assign DNS info on the Networked PCs too?
... cause I have NOT done that...

And how do I find what DNS info to type to the Networked PCs?
Thanks.

---

### Post by dvarsam on 2007-02-18
Hello again!

This is what I got from trying out "[color=blue]ipconfig /all[/color]" in Windows Terminal:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/WindowsNetworkingOutput.jpg[/IMG]

So, I tried to add the DNS info on the "[color=blue]Start\Control Panel\Network Connections\Local Area Connection\Internet Protocol (TCP/IP)\Properties[/color]".

I added the following:

```

Use the following IP address:
IP address: [color=blue]192.168.1.5[/color]
Subnet mask: [color=blue]255.255.255.0[/color]
Default gateway: [color=blue]192.168.1.1[/color]

Use the following DNS server addresses:
Preferred DNS server: [color=blue]192.168.1.1[/color]
 Alternate DNS server: [color=blue]empty[/color]

```

Is that correct?
After all these, I rebooted the PC & tried to connect to the Internet...
Nothing!!!
Not possible...

Do I also need to edit the properties of the icon named "[color=blue]1394 Connection[/color]" (inside the "network connections" window)?
Cause I have left that intact on both of the Networked PCs (default = Dynamic IP).

Thanks.

---

### Post by bulldog on 2007-02-18
DNS servers are provided by your ISP,you can set them in your router and use the DHCP option,this is the easy way.
If you want to have static IP's ,you'll have to dig in your papers to find your DNS adresses and put them in your DNS tab.

---

### Post by dvarsam on 2007-02-18
[QUOTE=bulldog]DNS servers are provided by your ISP,you can set them in your router and use the DHCP option,this is the easy way.
If you want to have static IP's ,you'll have to dig in your papers to find your DNS adresses and put them in your DNS tab.[/QUOTE]

Thank you very much for your reply!
I did NOT know that... :oops:
I managed to connect to the Router to get those...
I inputed them inside the required fields & now I have:

1. A WinXP <-> WinXP network that works
2. Each WinXP machine can access Internet.

Super!!!
Case Solved!!!

Now I am ready to attempt Networking an Ubuntu PC <-> WinXP PC
Thanks.

---

