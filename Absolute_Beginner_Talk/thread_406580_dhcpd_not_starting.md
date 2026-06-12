---
title: "dhcpd not starting"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-04-11
howdy.

i want dhcpd to only give an ip to certain mac addresses, i have another router giving dhcp for other pcs.

this is my config file, i think this is the reason it doesn't start, what is wrong?.

```
allow booting;
allow bootp;


#standard config directives

#option domain-name
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255
option domain-name-servers 203.0.178.191
option routers 192.168.0.1;




#PXE Bootable hosts
group {
        # pxe-specific config direct
        next-server 192.168.0.200;
        # pxe-specific config direct
        next-server 192.168.0.200;
        filename "/tftpbootp/pxelinux.0";

        host Earth {
                hardware ethernet 00:0C:29:84:A4:34;
                fixed-address 192.168.0.203;
}
}




```

---

### Post by kidders on 2007-04-11
Hi there,

One immediately obvious problem is that you're missing a few semicolons. Your system logs should've told you that though ... perhaps there is something else going on, other than errors in your config file?

---

### Post by 13ojo on 2007-04-11
nope i'd say its semi colons XD.

it said syslog, but it takes forever to find that stuff when you are 1) using console and 2) never used it before. figured out a setup that works :D. however im getting a weird quirk.

if i boot a pc into the netboot, it's given an ip, and it finds the PXELinux.0 file and boots. Nice and fine, runs nicely. However,

if the machine is reset, it seems to be given the same ip, but i get a PXE-T01: File not found error. Time seems to cure this, but it's weird. Must be something to do with dhcp requests/renewals?. I think i want the dhcp server to give out filename regardless, not just after big periods of inactivity..

---

### Post by kidders on 2007-04-11
> **13ojo said:**
> it takes forever to find that stuff when you are 1) using console and 2) never used it before.Try something like **tail -n 50 /var/log/syslog | grep dhcpd**.

> **13ojo said:**
> im getting a weird quirk.Hmm... I'm not sure about that one. The best way to find out what's happening might be to use a packet sniffer, so you can watch exactly what's going on.

---

### Post by 13ojo on 2007-04-11
restarted pc, works every time now :D. geuss some deamon needed to be restarted. i have some other problems, but they are now more related to the linux distro, rather than DHCPD and TFTP-HPA, so this thread is done :D.

---

