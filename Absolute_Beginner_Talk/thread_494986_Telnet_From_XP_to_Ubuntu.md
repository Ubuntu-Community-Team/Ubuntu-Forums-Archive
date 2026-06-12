---
title: "Telnet From XP to Ubuntu"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2007-07-07
Good Afternoon

I am attempting to Telnet within my LAN from XP to Ubuntu and receive "Could not open host on port 23"

When I attempt to ping the Ubuntu machine (ping 192.168.1.102) from XP, :(I receive "Request Time Out".

Thanks,
Frank

---

### Post by deepclutch on 2007-07-07
make sure firewalls dont come in btwn.

---

### Post by Frank_F on 2007-07-07
.thanks, I have disabled the XP firewall....do I need to do anything on the Ubuntu side ?

---

### Post by deepclutch on 2007-07-07
afaik ubuntu dont have iptables enabled default.but u can check by "iptables -L" and for flushing rules for current session as "iptables -F"
other reasons can be the ip range,subnetmask etc.check carefully.

---

### Post by Frank_F on 2007-07-07
...... I was  able to connect thanks for your help.

---

### Post by dbott67 on 2007-07-07
[COLOR=Purple]*EDIT: Nevermind! :)  I gotta learn to type faster!  Had you not figured it out, this is what I proposed:*[/COLOR]

In addition to the above, telnet is not installed by default in Ubuntu (or secure, for that matter).  If you want shell access, you should install openssh-server:
```
sudo apt-get install openssh-server
```Having said that, as deepclutch said, you should be able to ping the Ubuntu box if both are on the same subnet.  Can you confirm that both these machines are on the same subnet and that they have correct IP, subnet masks & gateway address?

Post the output of the following commands:

**1. For Ubuntu:**
```
dbott@feisty:~$ [COLOR=Red]ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:xx:xx
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:269711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:196289839 (187.1 MiB)  TX bytes:35631637 (33.9 MiB)
          Interrupt:16 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:697720 (681.3 KiB)  TX bytes:697720 (681.3 KiB)

```**2. For Windows XP:**
```
C:\WINDOWS>ipconfig /all

Windows IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com 3C920B-EMB-WNM Integrated Fast
Ethernet Controller
        Physical Address. . . . . . . . . : 00-0E-A6-BE-xx-xx
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.128.18
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.128.4
        DHCP Class ID . . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 192.168.128.25
```-Dave

---

### Post by Frank_F on 2007-07-07
Hello

Thanks for your guidance, yes they are on the same subnet. The strangest thing happend, when I disconnected my ethernet connection (laptop-XP) and went wireless in the backyard, I tried to ping the Ubuntu machine and it worked...I then issued the Telnet command and was able to connect.

As far as security goes, I currently have a router and am hoping that I am still secure as long as I stay within my LAN ?  Is this a correct assumption ?

Thanks Again,
Frank

---

### Post by atria on 2007-07-07
Glad it works now.

You should be fine as long as the connection is made locally without anyone (except your router) between your computer and your ubuntu machine. Do make sure that if you're using a wireless connection, try to use WPA/WPA2 instead of WEP.

In other words if the wireless connection is not encrypted, openssh will be far more secure than telnet.

I see no reason to use telnet instead of openssh in either case though, but thats just me, heh.

---

### Post by dbott67 on 2007-07-07
> **Frank_F said:**
> Hello

Thanks for your guidance, yes they are on the same subnet. The strangest thing happend, when I disconnected my ethernet connection (laptop-XP) and went wireless in the backyard, I tried to ping the Ubuntu machine and it worked...I then issued the Telnet command and was able to connect.

If you had both interfaces active/enabled (wired & wireless) there may have been some sort of problem.  Disabling the one that's not in use may make your troubles disappear.

> **Frank_F said:**
> 
As far as security goes, I currently have a router and am hoping that I am still secure as long as I stay within my LAN ? Is this a correct assumption ?

Thanks Again,
Frank

As for telnet & security, as atria says, as long as you can prevent others from accessing your LAN (thereby keeping it closed/private) telnet is okay.  However, if you use either or both computers to access the internet, then there is a potential vulnerability via worms, viruses, rootkits, etc.

I use openssh-server on Ubuntu and [PuTTy]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") or [Tunnelier]("http://www.bitvise.com/tunnelier") as the client when I'm in Windows.  Tunnelier also has a built-in SCP client (secure copy), whereas you'd need to download [WinSCP]("http://winscp.net/eng/index.php") if you use PuTTy.

So, a completely closed network would be safe to use telnet, but I'm with atria on this one --- install ssh.

Hope this helps.  For more information about remote access & security issues, read my "HOWTO's" below on Reverse VNC and Installing DenyHosts.  The Reverse VNC Howto is not secure, however, the thread gets into securing the connection, as well as [NX Machine]("http://www.nomachine.com/download.php").

-Dave

---

