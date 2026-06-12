---
title: "Starting DHCP server dhcpd3    [fail]"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Mwelsh on 2008-01-10
I get the message of Not configured to listen on any interfaces! in the syslog file.

Any suggestions? I'm very new to linux.

---

### Post by Mwelsh on 2008-01-10
I now have a working(or running) servr, but can't seem to get the PXE boot to work.... any suggestions?

---

### Post by stump138 on 2008-01-10
do you have the "next server" option set to your pxe server in your dhcpd.conf?

---

### Post by Mwelsh on 2008-01-10
Yes. As far as I can tell, I have the correct dhcpd.conf file. I know that the computers can see each other, because the link goes up/down when I reset the client. However, the DHCP doesn't seem to kick in and request or offer.

---

### Post by stump138 on 2008-01-10
can you post the contents of your dhcpd.conf please?  Also, is tftp installed and working on the pxe server?

---

### Post by Mwelsh on 2008-01-10
TFTP is installed and working.

here's the dhcpd.conf file:
> 
allow booting;
allow bootp;

ddns-update-style none;
ddns-ttl 86400;

option domain-name "tengTest";
option subnet-mask 255.255.255.0

subnet 10.0.0.0 netmask 255.0.0.0 {
   range 10.100.1.100 10.100.1.200

   default-lease-time 86400;
   max-lease-time 864001;
}

#PXE Bootable Host
next-server TFTP_SERVER_IP_ADDRESS;
next-server 10.0.0.1;
filename "/tftpboot/pxelinux.0";

host tengM {
   hardware ethernet 00:18:8b:07:2f:06;
  fixed-address 10.0.0.1;
}


---

### Post by stump138 on 2008-01-10
change your settings to this and try it out.  Also is your PXE server the same one as your DHCP server? or is it on a separate box?

```

#PXE Bootable Host
filename "pxelinux.0";
next-server 10.0.0.1;

```

---

### Post by Mwelsh on 2008-01-10
same box

---

### Post by Mwelsh on 2008-01-10
Remove the TFTP_SERVER_IP... as well?

> **stump138 said:**
> change your settings to this and try it out.  Also is your PXE server the same one as your DHCP server? or is it on a separate box?

```

#PXE Bootable Host
filename "pxelinux.0";
next-server 10.0.0.1;

```

---

### Post by stump138 on 2008-01-10
I've never seen anyone using that setting, worst case is you have to add it back in :)

---

### Post by Mwelsh on 2008-01-10
sadly, after those changes, no luck. Could it possibly be something to do with my eth0 settings? 

Currently, 

> 
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.0.0.0


From my understanding, for a PXE boot, you use a DHCP server to send a packet to the computer that wants to PXE boot. It then receives the kernel to boot from, and you're off to the races.... However, let me know if my understanding is wrong!

---

### Post by Mwelsh on 2008-01-10
Additionally, I also have the Client and Server DIRECTLY connected with ethernet as opposed to through a switch. I'm not sure if this matters or not, but when the server is functional it will be done through a switch so that multiple clients can access it.

---

### Post by stump138 on 2008-01-10
I use a switch personally, but I wouldn't think that it would impact your performance.  Are your clients generating an error when you try to PXE boot it?  Is the client machine first recieving an IP address from the dhcp server?

---

### Post by Mwelsh on 2008-01-10
The client machine is getting nothing. I get the message to Select a Proper Boot device or Reboot, something along those lines. I don't believe it is receiving a kernel or any packet from the server.

So I guess it is getting no IP address, and in fact likely nothing. Does this mean the server is not listening properly? Or is it possibly blocking the clients?

---

### Post by stump138 on 2008-01-10
Are you trying to run LTSP by chance?  If so I can point you in the direction of some great stuff to work with that.

I would remove the stuff about PXE booting for now and just see whether or not you're even handing out addresses from the dhcp server.  You may not even be getting to the PXE portion of it yet.  I'd also throw a switch in between with a connection to the internet (if you can) to test out the dns and gateway portions of your DHCP settings.  Then you can work your way toward the pxe settings.

---

### Post by Mwelsh on 2008-01-10
The /var/log/syslog file of the connection looks as such:

> 
Jan 10 15:42:43 tengM kernel : [ 9383.502708] e1000: eth0: e1000_watchdog: NIC Link is Down
Jan 10 15:42:45 tengM kernel : [ 9383.502708] e1000: eth0: e1000_watchdog: NIC Link is Up Mbps Full Duplex, Flow Control: RX


I can tell this is from a connection change of sorts since this occurs whenever I reboot the client computer, so it does recognize something.

---

### Post by Mwelsh on 2008-01-10
This is an isolated system with no access to the internet unfortunately. I don't know what you're talking about the LTSP, I'm a little lost there sorry. I've only been on Linux for 3 days, but a server is my first task. I believe addresses are NOT being handed out...

---

### Post by stump138 on 2008-01-10
well the first thing you should do then is place a switch between the server and the client.  Now start the client using any OS, it's not important atm.  See if it picks up addressing information from the server.  Make sure the dhcp server is running by
```
sudo /etc/init.d/dhcp3-server restart
```

and make sure that it is up and running

---

### Post by Mwelsh on 2008-01-10
I don't have an OS for my client unfortunately. I have reset the server (a couple times, I reset it whenever I make changes such as the ones you suggested earlier). Perhaps I'm just out of luck?

---

### Post by stump138 on 2008-01-10
are you trying to PXE boot a thin client?  if so, try [this]("https://help.ubuntu.com/community/ThinClientHowto")

---

### Post by Mwelsh on 2008-01-10
Yes. and if not that, something very similar. I will look over those pages and try to solve it. Thank you very much for all your help.

---

