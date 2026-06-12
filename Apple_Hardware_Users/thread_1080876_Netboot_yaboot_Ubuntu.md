---
title: "Netboot yaboot Ubuntu"
date: 2009-02-25
forum: Apple Hardware Users
---

### Post by marconeuro on 2009-02-25
"Maybe, someday, five thousand years from now, aliens digging through the remains of human civilizations will be interested in this information, so I'll leave it lying around here." (nice, I lent the quote from a similar post)

I have one ibook G3 12 inch dual usb. After the latest Mac tiger crash just decided to go on Ubuntu. I don't have a cd writer, the usb bootup won't work on the ibook, then the only solution is netboot. (boot from network) There is plenty of guide of this item, but none work correctly. 
follow this:
[https://help.ubuntu.com/8.10/installation-guide/powerpc/install-tftp.html#tftp-images](https://help.ubuntu.com/8.10/installation-guide/powerpc/install-tftp.html#tftp-images)
There is better guide on the net anyway

1. Set up tftp on Ubuntu:
after doing 
apt-get install tftpd-hpa tftp-hpa

 you need to open the firewall on port 69 with 

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 69 -j ACCEPT

2. set up dhcp server:
sudo apt-get install dhcp3-server
sudo vi /etc/dhcp3/dhcpd.conf
add 
allow booting;
allow bootp;


subnet 192.168.0.0 netmask 255.255.255.0 {
        allow bootp;
        range 192.168.0.100 192.168.0.200;
        next-server 192.168.0.2;
        filename "yaboot";
}
(my ipaddress is statically assigned  192.168.0.2)
sudo vi /etc/default/dhcp3-server
add
INTERFACES="eth0"
sudo /etc/init.d/dhcp3-server restart
go to /var/lib/tftpboot
I don't know if it is necessary, but change owner and group of the directory of your user or nobody
do:
cd /var/lib/tftpboot
sudo lftp -c "mget http://ports.ubuntu.com/ubuntu-ports/dists/intrepid/main/installer-powerpc/current/images/powerpc/netboot/*"

Here the problem. The yaboot present on the server won't work, you have to download a working one, and substitute it: (I tryed to open a bug report, but the server is currently down)
[http://launchpadlibrarian.net/19944818/yaboot](http://launchpadlibrarian.net/19944818/yaboot)
substitute your yaboot.
start the Mac in open firmware:
opt+command+o+f at startup
do:
boot enet:192.168.0.2,yaboot

and then, this time, you can do your slow network installation....

"The Magic is in the Movement"
[http://machicecaga.blogspot.com/](http://machicecaga.blogspot.com/)

---

