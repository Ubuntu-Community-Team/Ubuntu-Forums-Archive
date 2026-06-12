---
title: "Basic network stuff?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Bartender on 2005-12-23
Good day -
Tried to network the W2K machine to the UL5.1 machine this morning.  I've no experience networking.  About one hour with Linux.  All the acronyms - PAP, CHAP, DNS, DHCP - make my head hurt.  
My primary Linux goal at this point is to network these two together and see if I can get the UL5.1 box online via the W2K machine.    
Not using a router, just a X-over cable.  Seems like most folks on these forums are using routers.  If I'm on dial-up is there any reason to get one?
Didn't know if I should shut the machines off before jacking in the cable, so took a chance and just plugged it in.  W2K immediately noticed something was different.  The little icon in the lower right-hand corner changed.  Right-clicked on it, asked for "Status", got the "Local Area Connection Status" box.  W2K is sending packets but not receiving.  
Turned to the UL5.1 box.  I had mlomker's "Wired Ethernet Troubleshooting Process" in hand.  I entered various commands as you can see below.  
It looks to me like Ubuntu is O.K. with the NIC.  Hopefully the rest is just operator education??
Kinda funny...I was easily able to ask Ubuntu for the hostname (127.0.0.1), but haven't been able to do this in W2K.  I'm pretty sure all this is basic but I'm floundering.
Oh, yeah, the little lights on UL5.1's NIC are working.

When I tried "eth0 up" there was no response.  When Ubuntu does nothing with a command and just flashes right back to the initial input line, what does that mean?  I don't know if I goofed up the command or what.

"man networking" didn't get me anything either.

Thanks


pattibarmettlerpatti@ubuntutoots:~$ ip link show
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:50:da:8e:54:ef brd ff:ff:ff:ff:ff:ff
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0
pattibarmettlerpatti@ubuntutoots:~$ hostname -i
127.0.0.1
pattibarmettlerpatti@ubuntutoots:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok
pattibarmettlerpatti@ubuntutoots:~$ sudo ifconfig eth0 up
pattibarmettlerpatti@ubuntutoots:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:DA:8E:54:EF
          inet6 addr: fe80::250:daff:fe8e:54ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:5 Base address:0xb000

pattibarmettlerpatti@ubuntutoots:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
pattibarmettlerpatti@ubuntutoots:~$

---

### Post by stuporglue on 2005-12-23
Do you just want to connect the two computers, or do you want to share internet from the dialup computer to the other computer? 

If you just want to connect the two computers, it's easiest to just set both computers IP addresses manually. 

Set both of the computer's subnet addresses to 255.255.255.0. Then set the IP address of one to 192.168.0.1 and the other to 192.168.0.2. As soon as you apply the changes, they will be on the same network. 

Getting them to communicate will depend on what you want to do with them. For example, if you want to be able to ssh from the Windows to the Linux, you'll need to install an ssh server on the Linux, and get a ssh client for Windows. You'll need to do a similar thing for whatever type of server you want to use (SMB --Windows file sharing, HTTP -- Web server, ftp, whatever).

---

### Post by cstudent on 2005-12-23
The suggestion of setting static ip's is probably the easiest thing to do. You'll need to go into the W2k machine>Control Panel>Network & Dialup Connections and right click on your network icon. You should see a tab for sharing. You'll need to turn on internet connection sharing. You may also need to setup a dns server (Control Panel>Administrative Tools), but I'm not 100% sure about that. Your gateway for the Ubuntu machine would be the ip of the W2k machine.

---

### Post by Bartender on 2005-12-23
[COLOR="SeaGreen"]"Do you just want to connect the two computers, or do you want to share internet from the dialup computer to the other computer?"[/COLOR]

Yes to both

Aagh, stuporglue, the ease with which you left me in the dust is somewhat demoralizing.  "ssh"?  What's that?  SMB, HTTP - more acronyms, the meanings of which I barely grasp.  
I'll google ssh and educate myself if possible.
It sounds like manually creating IP addresses as you describe won't get the L box online via the W box, but there's no harm in trying to enter those settings, is there?  See if I can make something happen?  Small successes build confidence.
I see a lot of posts about repositories, dependencies, apt-get, etc.  With no internet connection to the L box I'm on the far side of the creek from all that fun.  If "ssh" is a program, and I need to download that, is it a stand-alone package?  What I mean is, can I download it to my flash drive, bring it over to L, drag it to the Desktop or some such, and get L to install it?  I'm sure you understand what I'm getting at - without the ability to have apt-get or Synaptic handle the job, how do I know I got what I need?  I've seen (and initiated) posts regarding slow/no internet connection, but haven't really seen any good answers.  Or at least ones I understood;)

EDIT: I'm a widdle bit newvous about this - I'm not gonna screw up W's ability to go online by dinking around with IP settings, am I?

---

### Post by Bartender on 2005-12-24
Tried giving static IP's to both machines.  Had some limited measure of success - the W status window "Received" number shot upward when being pinged by L, but L indicated 100% loss when it was done.  I saw W sending small bursts in between the receiving.
W pinged L, and said 0% loss.  But I couldn't find any place on the L machine to verify this.  I'm now getting "DHCP" warnings in W2K's Event Viewer - "Your computer has automatically configured the IP Address for the network card with network address 0011D85BF691.  The IP address being used is 169.254.128.141"
Scrolled back thru history, this is new.
I don't understand the first set of numbers.  The second set is recognizable at least.
I set W back to "DHCP" instead of static.  Did the same for L.  Ipconfig'ed and ifconfig'ed, got some IP's to try.  But pinging doesn't seem to work as well now.

- Can anyone please explain - L shows two network devices, lo and eth0.  What's loopback?  No entry in man for that.  eth0 shows no IP address, lo is 127.0.0.1

- W does recognize something happening - the network icon in systray goes from disconnected to showing two monitors as soon as the L machine gets started.  At some basic level it's seeing the other machine.

-L seems to be acting dodgy with saving settings.  I turned it on this morning and the NIC was back to static instead of DHCP.  Is there an extra step I'm missing to make it save the settings?  Wait a minute, maybe all I have to do is back all the way out of the network settings windows.  

- When I'm at "Interface properties" (System>Administration>Network Settings>Interface properties) the "Help" life preserver doesn't do anything.  I back up one window to "Network settings" and Help still doesn't work, but at that stage I get an error message saying "Could not display help - unable to find help files in either usr/share/gnome/help/shares-admin/shares-admin or usr/share/gnome/help/shares-admin".  OK., this is getting weirder.  last night I got the error message.  This morning I was able to access help in the "Network Settings" window, but still not at the "Interface properties" window.

- I tried apt-get samba, expecting it to try to go online, but it installed samba.  Cool.  After that, I went to System>Admin>Shared Folders>Add, hoping to get W and L talking to each other.  The window shows a path, which looks OK (home folder), shares with SMB, then under share properties I have Name and Comment.  The "OK" button is grayed out.  I don't know what to enter here.  Oh, yeah, I tried apt-get smbfs, and it's not there.  Do I have to get that from the internet before shared folders will work?

ifconfig, hot off the presses:

eth0      Link encap:Ethernet  HWaddr 00:50:DA:8E:54:EF
          inet6 addr: fe80::250:daff:fe8e:54ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9235 (9.0 KiB)  TX bytes:12096 (11.8 KiB)
          Interrupt:5 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:660957 (645.4 KiB)  TX bytes:660957 (645.4 KiB)

---

