---
title: "[SOLVED] pxe-T01: File Not Found"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by LRT on 2008-03-27
I'm trying to set up a thin client server on Ubuntu 7.10 (not Edubuntu) and I am following this howto ([https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")) the howto is fairly straight forward but doesn't seem to be working for me.

when i boot my client i get this error:

PXE-T01: File Not Found 
PXE-E3B: TFTP Error - File Not Found
PXE-M0F: Exiting Intel Boot Agent

I've looked at numerous post on this forum and have tried changing the path to the pxelinux.0 file but this has had no effect.

this is what i have in my dhcpd.conf file:

```
subnet 192.168.18.0 netmask 255.255.255.0 {
   range 192.168.18.11 192.168.18.50;
   option routers 192.168.18.10;
   option domain-name-servers 192.168.1.1;
   option root-path "/opt/ltsp/i386";
   filename "/boot/pxelinux.0";
}
```

i also have three pxelinux.0 files located on my server, and i don't know which one to use...

```
root@pandion:/# find / -name "pxelinux.0"
/opt/ltsp/i386/usr/lib/syslinux/pxelinux.0
/opt/ltsp/i386/boot/pxelinux.0
/var/lib/tftpboot/ltsp/i386/pxelinux.0
root@pandion:/# 

```

i'm also not sure what services i shoud stop/start after i change the dhcpd.conf file ((other than /etc/init.d/dhcpd.conf restart). is there a tftp service i need to restart??

anyone have any ideas?? thanks!!

---

### Post by LRT on 2008-03-28
ok, i figured it out. I followed this howto instead [(https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall") which installs a standalone DHCP server alongside LTSP (/etc/ltsp/dhcpd.conf). i didn't have a prexisting DHCP service installed so there was no conflict. 

the howto i was using before (see first post) gives you two options when installing/configuring the DHCP server. If you have an existing DHCP server than all you have to do is add the following lines to your subnet declaration:

```
filename "/ltsp/pxelinux.0";
option root-path "/opt/ltsp/i386";
```

but this wasn't working for me because i kept getting "pxe-T01: file not found" error messages on boot, so instead i tried installing ltsp-server-standalone and this worked flawlessly. hope this works for someone else out there. playing with a thin client setup is very nice!

---

