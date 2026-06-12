---
title: "[SOLVED] How to connect VMWare Guest OS to internet on host"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by fenixphire07 on 2007-11-20
Hi guys, I'm on the verge of ditching windows permanently especially after i heard of this app VMWare Server.

I followed the how to in Tutorials and Tips and got it installed on my Ubuntu 7.10.

So this is the situation right, I have Ubuntu as the host (its my primary OS) and i installed XP Pro on VMWare. 

My internet is a PPPOE requiring a user name and password. I'd love for both these OS's to share, but if not what else can i do. I dnt know much abt networking and even less on networking on Ubuntu. so pls help me. 

thank you.

---

### Post by rmemm on 2007-11-20
I've used VMWare under windows as the guest OS and Linux as the host -- I assume they are the same -- but with the OSes reversed.  So what I'm going to say is from my experience with that.

In the VMWare network setup -- you can define a number of types of network connections.  These include bridged (the guest vm will be like it's directly on the network -- and will need it's own IP), local (guest is on an isolated network -- not connected to the lan), or NAT which creates a setup where the guest is on it's own local network, but it connects to the internet through a virtual router.  

I use the last configuration myself (NAT) as it shares the same IP address space as the host OS and so if you can connect to the internet with the host then you should be able to connect via the guest.  This works well unless you want to publish network services to the outside world (like putting up your own web server for example).  If you want to do that you have to specifically go into the VMWare setup and map ports on the host system back to the port and ip of the guest VM so that the data gets routed properly.  If you want to go outbound -- which is what most people would want to do however -- then you usually need to do nothing special in the NAT case (there are of course a few exceptions -- like bittorrent for example).

Does this make any sense?

Rob

---

### Post by fenixphire07 on 2007-11-20
I'm sorry, but it doesnt to me :( not the sharpest tool in the shed am I.

Anyway, i thought i'd play around with the VM settings for the VM and hopefully something will click. on the bridged option does not through an error, saying the file is missing vmnet1, vmnet8. i checked the filesystem and the only one available is vmnet0 - which i assume is the bridged one.

is it a problem with how i installed vmware. if so can someone direct me towards how to uninstall it and then reinstall some other way. thanks

---

### Post by rmemm on 2007-11-21
Sorry.

Just opened up my VMWare Server Console -- the user interface to VMWare Server.  I'll take a look at my settings -- and you can see if you have something the same.

Under VM>Settings...>Hardware>Ethernet I have "Network Connection" set to NAT.  I think one could use Custom as well and select the VMNet8 (or whichever one is using NAT).

Having VMNet1 and 8 missing in your setup is strange.  On my setup VMNet1 is Local Host only which one would think should always exist, and VMNet8 is NAT again one of the standard defaults usually.  These actually can all be swapped around -- too -- but at least on Windows they always default to 0, 1, and 8 being bridge, local, and NAT, and the others being nothing specific.

Then in Host>Virtual Network Settings...>Host Virtual Network Mapping you can adjust the network assignments of VMNet0...VMNet9.  As I said before mine has 0,1, and 8 at the defaults.  It's possible that for Linux these need some sort of special setup.  For example -- perhaps they need to somehow be setup to use the ether tap device -- if so -- perhaps there is something in the Doc about this.  On windows this is automatic.

If you do use NAT then there is some configuration to do in the NAT, DHCP, and Subnet dialogs.  I think on windows though the defaults were pretty good as long as you set up your windows Guest OS to use DHCP to get it's IP address.  This is typically done in one of the windows control panel tools.

You should be able to use Bridging also -- but I don't know if the connection to your ISP will allow you to do that.  I connect to my ISP through a router box which means I can have any number of computers on my local network -- but if your using some sort of single computer connection -- this may not be allowed.  Kind of depends.  If you have a setup like I have -- then bridging will work -- but I don't know about your case.  The thing to remember with bridging -- both the Host OS and Guest OS will look like two totally separate computers.  Whatever you'd have to do to make that work is what you need to do to make the VMWare setup work for bridging.

Rob

---

### Post by fenixphire07 on 2007-11-21
hey rob, thanks for all your support. I have to say i have to give ubuntu forum support :KS:KS:KS (full points)

Ya well, it seems i had said yes only to bridged network when installing. BUT now I reinstalled and got it working.

so thanks rob.

---

### Post by fenixphire07 on 2007-11-21
Well, since this aint a blog :D i suppose i should enlighten those who are or will be in the same boat as i was

Firstly, if your your vmnet# is missing (# being a numeric number) then probably you have not installed it properly. You can uninstall it by simply  attempting to reinstall this, or else uninstall vmware server by following these steps

open the terminal
cd temp/vmware-server-distrib      {this is the place you extracted your tar.gz setup file}
cd /bin 
sudo ./vmware-uninstall.pl

at this point, vmware server is completely out.

then start reinstallation, follow (HOW-TO in Tutorials and Tips Forum)

try to pay attention after the agreement part, thats where the stuff get installed.

install one of each type of network, bridged, host, NAT

then install windows. 

ok at this point, you have everythhing going but two problems

NO 1: if you have set up your ethernet as NAT - then u have internet but cannot connect to host

NO 2: if you have host-only, then no internet.

so this is what you do. install windows and then install the VMTools (optional the vmtools not the windows) :)

after that, power off your virtual machine. next do

         windows tab > edit virtual machine settings

in all probability you will have only one ethernet in this, wat you do is add another ethernet card. and then set one to host-only and the other to NAT

u can now use host-only card to connect to ubuntu and the nat for the internet

oh and finally, the port for internet is 902 (for utorrent fans)

any other questions leave posts here or pm me, i will try to help :) no promises

---

### Post by rmemm on 2007-11-21
Great!

One note -- in fact you can access the local host from the NAT subnet without using a second localhost network.  I can't remember, the IP address for certain, but if you have a subnet for NAT thats is for example 192.168.2.0/255.255.255.0 - then there are two IP addresses one for the virtual router's gateway address, and one for the host host os -- I think they are 192.168.2.1 and 192.168.2.2 -- don't know which is which. It describes this in the VMWare doc somewhere.

If your using a different subnet scheme then the addresses are modified accordingling -- typically ending in .1 and .2 I think.  Maybe setable in the options dialog too.

Anyway I do agree though it's good to install all 3 bridging, local, and NAT so you have a choice.

Take care,

Rob

---

