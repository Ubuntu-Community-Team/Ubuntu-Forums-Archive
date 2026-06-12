---
title: "Help w/ Thin client Please!"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-02-02
Hello, (Edubuntu 7.10)

I followed [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted) as a guide, everything on the server seems to be working fine and I downloaded the updates.

When booting a thin client it finds the server and begins to boot.  I get to the Edubuntu loading screen, it stops then  gives me 

BusyBox v1.1.3 shell stuff and a command prompt 
(initramfs)

I hit crt+alt+f1

I see the 
Loading, please wait...

Then displays the IP-Config stuff and gives me my ip address, broadcast, netmask, gateway, dns0, dns1 domain, rootserver

It then shows that it tried to mount things
"Mounting /rofs on /root/rofs failed:invalid argument
Mounting /root/dev on /dev/.static/dev failed:no such directory"
and a couple other mount failures

I am assuming that my dhcpd.conf file is pointing it to the wrong place or something.  I am trying to boot them through a switch with other computers connected.

Any help is appreciated.

---

### Post by ivomans on 2008-03-07
I got exactly same "Mounting /rofs ..." error. Occurred after I tried to upgrade the thin-clients to Gutsy. Couldn't find any useful help on the net, but after a few hours I solved it with following sequence of commands:
```
cd /var/lib/tftpboot/ltsp
sudo mv i386 i386.old
cd /opt
sudo mv ltsp ltsp.old
sudo ltsp-build-client
sudo cp /opt/ltsp.old/i386/etc/lts.conf /opt/ltsp/i386/etc/

```After this everything was running fine. You could clean up then with:
```
sudo rm -Rf /var/lib/tftpboot/ltsp/i386.old
sudo rm -Rf /opt/ltsp.old
```Especially removing the directory under tftpboot seems to be of high importance.

---

