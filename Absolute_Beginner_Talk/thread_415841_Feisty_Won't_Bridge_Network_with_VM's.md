---
title: "Feisty Won't Bridge Network with VM's"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-04-20
I've tried VMware and Virtualbox and neither of them are bridging my network connection. I went back to Edgy 
and it worked fine. When the final release of Feisty was released, I tried again..I'm still not able to bridge my 
network connection. I'm sure it's not my virtual machines or the software, but a feisty/kernel issue.

Any idea what could be wrong? I've reconfigured VMware and Virtualbox many times making sure the right 
interfaces are set to bridge. Nothing seems to work.

Thanks for your help!

---

### Post by shanepardue on 2007-04-20
From what I gathered, the only VMware that works without a workaround is VMware Workstation 6 Beta that is 
free. The workarounds for server and player didn't allow for bridged network connections at least in my case.

VMware Workstations 6 Beta works fine with Feisty

---

### Post by pviglucci on 2007-04-21
> **shanepardue said:**
> The workarounds for server and player didn't allow for bridged network connections at least in my case.

I'm running vmware-player on Feisty and bridged networking is working fine.

Are you absolutely sure that you are bridging the correct interface?  A very common problem that occurs with laptops is that the ethernet connection is configured as eth0 and the wireless as eth1.  Automatix, for example, will set the bridge up on eth0.  If you use wireless all the time then the bridge will not work.

You can run "ps -ax | grep -i bridge" to see to which interface the bridge is attached.  The output will look something like this:

11110 pts/0    S      0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0

The interface is indicated at he end of the line (eth0 in this case).  If you want to bridge to eth1 instead, modify /etc/vmware/locations and replace the instances of eth0 with eth1.  Restart the the vmware service (/etc/init.d/vmware-payer restart) and run the ps command again.  The output will be something like:

11110 pts/0    S      0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth1

Fire up your virtual machine and bridged networking should be working.

---

### Post by shanepardue on 2007-04-21
Yeah..I did check the interfaces. I noticed it worked on my desktop, but not on my laptop. I bridged both my eth0 and eth1 to no avail. I'm not really needing a fix anyway because workstation 6 beta works perfectly.

Thanks for your help!

---

### Post by bodhi.zazen on 2007-04-29
shanepardue: 

I believe the problem is with networkmanager.

see here for how to disable networkmanager without uninstalling : 

[http://doc.gwos.org/index.php/VirtualBox#Trouble_shooting](http://doc.gwos.org/index.php/VirtualBox#Trouble_shooting)

---

### Post by shanepardue on 2007-04-29
That makes sense..Fortunately, I don't have the problem anymore since I've used VMware workstation and it works right along with NetworkManager so I'll stick with that..thanks!

---

### Post by veloce on 2007-05-01
And my upgrade to Feisty caused no problems with my bridged network.

---

### Post by bullgr on 2007-05-01
> **shanepardue said:**
> From what I gathered, the only VMware that works without a workaround is VMware Workstation 6 Beta that is 
free. The workarounds for server and player didn't allow for bridged network connections at least in my case.

VMware Workstations 6 Beta works fine with Feisty

i have the same problem like you...
vmware server 1.0.2 don't work without patched and after the patch i can't networking ubuntu host from and to vm.

i tried also vmware workstation 6 beta and worked perfect. but free?
you can downloading it and get a serial number license for 30 day's. after that you must buy it for 189$.
go to help>about and see the license you have and when expires.

vmware player and server are free, but not workstation...

---

### Post by veloce on 2007-05-01
> **bullgr said:**
>  i can't networking ubuntu host from and to vm.


So what fails?  I had some issues with the built in dhcp server not providing a gateway address, but I switched vmware's dhcp server off anyway.

---

### Post by bullgr on 2007-05-02
in edgy i used the bridged option in network to see the samba shares from host and the other pc in my network.
after i upgrade to feisty the vmware server 1.0.2 version don't work anymore (don't support the new 2.6.20 kernel).
and after the any-any patch or the clean vmware server install from ubuntu repos (included the precompiled kernel modules for vmware server)
with the bridged option i couln'd connect to the host shares. only to the other pc in my network.

this is a issue in the patch and the precompiled kernel modules and nothing from my setups (router, samba, ip's).
when i install vmware workstation all work perfect. i can bridge anywhere.
but like i wrote above, workstation is not free. after the 30 day limit you must pay 189$.

the only sollution to see the host shares is to use nat in the network options and get automatic ip in virtual mashine.
but to connect to the other networked pc's you must give the ip and not theyr network name.
for example you can't connect to the network pc "PC2" (ip 192.168.0.2) direct. but if you give the ip 192.1668.0.2, then you can see the PC2 shares.

---

### Post by zdude on 2007-05-02
Hmmm, I did the upgrade and my virtualbox bridge networking is working fine.

---

### Post by veloce on 2007-05-02
> **bullgr said:**
> in edgy i used the bridged option in network to see the samba shares from host and the other pc in my network.
after i upgrade to feisty the vmware server 1.0.2 version don't work anymore (don't support the new 2.6.20 kernel).
and after the any-any patch or the clean vmware server install from ubuntu repos (included the precompiled kernel modules for vmware server)
with the bridged option i couln'd connect to the host shares. only to the other pc in my network.

this is a issue in the patch and the precompiled kernel modules and nothing from my setups (router, samba, ip's).
when i install vmware workstation all work perfect. i can bridge anywhere.
but like i wrote above, workstation is not free. after the 30 day limit you must pay 189$.

the only sollution to see the host shares is to use nat in the network options and get automatic ip in virtual mashine.
but to connect to the other networked pc's you must give the ip and not theyr network name.
for example you can't connect to the network pc "PC2" (ip 192.168.0.2) direct. but if you give the ip 192.1668.0.2, then you can see the PC2 shares.

This last behaviour sounds like the vmware dhcp server is not setting the dns address.  I had an issue with the dhcp server being on (and not supplying the gateway address).  I don't use the vmware dhcp server, I have a virtual firewall to keep my vms from tto much interaction with  the work network.  Turning off the dhcp server is a bit of a mission, I found instructions here:

[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article)

When I upgraded to feisty, dhcp seemed to have turned on, but when I went to look at the config, it was still "off".

RELEVANCY: After looking at the config file I, for no apparent reason, decided to restart the virtual networking service using the last instruction:
```
sudo /usr/lib/vmware/net-services.sh restart
```
and the dhcp server turned off.

SO: I suggest you restart the network service with the above command.

---

### Post by bullgr on 2007-05-04
> **veloce said:**
> This last behaviour sounds like the vmware dhcp server is not setting the dns address.  I had an issue with the dhcp server being on (and not supplying the gateway address).  I don't use the vmware dhcp server, I have a virtual firewall to keep my vms from tto much interaction with  the work network.  Turning off the dhcp server is a bit of a mission, I found instructions here:

[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article)

When I upgraded to feisty, dhcp seemed to have turned on, but when I went to look at the config, it was still "off".

RELEVANCY: After looking at the config file I, for no apparent reason, decided to restart the virtual networking service using the last instruction:
```
sudo /usr/lib/vmware/net-services.sh restart
```
and the dhcp server turned off.

SO: I suggest you restart the network service with the above command.

the only option to see the host shares in the vm is to get auto ip in vm and use nat...
this is an issue of the patched vmware server in feisty. if i install vmware workstation all works perfect. i can bridge anythere.

i tried anyway the method you suggest but after the command
sudo /usr/lib/vmware/net-services.sh restart
nothing changes and if i turn off the dhcp the bridged problem still remains, and ever worse, the nat aren't worked too.

i can't understand, in edgy vmware server was working perfect with bridging, in feisty workstation too, but
the patched vmware server version in ubuntu repos does not.
no matter i make a fresh install, remove totally, fresh install again, i get no bridging.

i hope they release soon a new version, supporting the new 2.6.20 kernel.

---

### Post by finite9 on 2007-09-18
Is this a kernel issue?  Im not sure if I have multiple issues, but here goes...

I used Dapper Drake with VMware player and it worked fine in bridged mode.  I use WinXP guest purely for connecting to employers VPN server.

I now run Feisty, and during Herd releases I decided to go over to KVM.  I installed KVM and did not remember if I chose specifically bridged or NAT mode, but my Nortel Contivity VPN software worked fine in KVM on a wireless connection with NetworkManager.   I never tested vmware server on feisty as they said that the kernel modules would not work in 1.02

Several months have gone by and I have not tested.  Now I go back to work after parent leave and try to use vpn in KVM and it wont work!  Cannot ping vpn IP address or DNS name.  KVM gets NAT address and is not using bridged...I do not know how to make it use bridged.

I decide to install vmware server from feisty repos, and use bridged mode, and i install a new XP images, and vpn will not work!  Vmware gives NIC 169.254 address, not a DHCP address from my router!

I install VirtualBox and test in both default NAT mode and bridged mode accoding to Ubuntu wiki, and VPN does not work.  Bridged mode gives NIC 169.254 address and not a DHCP from my router.

I am assuming that my VPN is not working because it NEEDS to resolve DNS to IP and uses IP, and NAT mode cannot contact IP's in virtual solutions.  I assume that I NEED to get bridged networking to work, like it did in dapper drake, but for some reason I am not getting an IP from my router.

Maybe I can download VMware from the official site instead of using feisty repos, and build the kernel modules myself??  maybe this will make bridged mode work like it used to in dapper drake?

Note that if I run Winxp native, just booting from laptop, and start my VPN then it connects OK, so I do not think this is a home networking/DHCP/router issue.

---

