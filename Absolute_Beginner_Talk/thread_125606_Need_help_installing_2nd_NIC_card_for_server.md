---
title: "Need help installing 2nd NIC card for server"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by dlafary on 2006-02-04
I have successfully loaded the server package. During the installation the software detected both network interface cards. One was the realtek from D-Link and the other was the onboard eithernet Marvell adapter. I selected the D-link because it was a 10/100 and would interface the internet since my cable modem only puts out 10mbs anyway. I reserved the internal network interface card (Marvell) which is a gigabit adapter for the internal network. I discovered after the install that the network interfaces file has only one interface defined. Eth0 which is the D-Link only. My question is:
has the marvell interface card driver been loaded and is simply awaiting configuration? Or do I have to loaded it? Is there a parameter file that shows which adapters have been loaded?  Can someone point to a howto that describes the procedure in installing a second network interface card into the server?  Any Ideas would be appreciated.
:-k

---

### Post by Dan Luevano on 2006-08-16
i was able to install a second NIC card, by editing the following files:

/etc/network/interfaces
/etc/iftab

now both my cards appear when I boot, but the problem I'm having is that my second NIC card (connected to the internet with a static IP) stops responding when my first NIC card (eth0) is UP. If I bring eth0 DOWN, then eth1 starts accepting requests from the internet.  It's weird and I haven't been able to solve this yet.

If you have more questions you can email me directly at [email]dan@twinvisioninc.com[/email]

Regards,

Dan Luevano

---

### Post by Maddman on 2006-08-17
I am having this same problem - when one card is active, the other is completely dead.  I'm not even showing a MAC address on the switch!

---

### Post by Dan Luevano on 2006-08-17
Let me ask you...have you used 'ethtool' to look at your devices? use: 'ethtool eth0' and it shows you some info about the nic card.  i'm curious to know if both your cards show the same PHYADR.  Mine do...and i'm trying to find out if that is a bad thing.

Thanks.

Dan

---

### Post by HwyXingFrog on 2007-02-08
Has anyone mastered this yet.

I have a quite confusing network, but this is basically the gist of it.

I have my main internet coming in, and then going to a switch (this allows my Ubuntu Web Server to obtain a different public IP than my Wireless router).

So, my Ubuntu Web Server has 100% of it's ports open on eth1. (Plugged into Switch)
My router is then plugged into the switch.

The router is where I do all my home file sharing and wireless networking and also had a gigabit switch in it.

I want to be able to use eth0 on my Ubuntu Server, and connect it to my gigabit switch (LAN).

Right now my eth1 has a public ip, and eth0 has LAN IP.

Eth1 works fine for web hosting until I connect eth0 and do 'sudo /etc/init.d/networking restart'

Once I do this all traffic attempts to go through eth0 (which is on my LAN)

I know this is confusing, but hopefully it makes sense to someone

Is there a configuration file I can change to set which NIC is used for what?

---

### Post by HwyXingFrog on 2007-02-08
I just tried this command (the middle one), and now I can access my web server publicly.

~$ ip route
142.165.220.0/24 dev eth1  proto kernel  scope link  src 142.165.220.5 
192.168.123.0/24 dev eth0  proto kernel  scope link  src 192.168.123.102 
default via 142.165.220.1 dev eth1 
default via 192.168.123.254 dev eth0 

~$ sudo ip route del default via 192.168.123.254 dev eth0

~$ ip route
142.165.220.0/24 dev eth1  proto kernel  scope link  src 142.165.220.5 
192.168.123.0/24 dev eth0  proto kernel  scope link  src 192.168.123.102 
default via 142.165.220.1 dev eth1

Is there any way to permanently remove that default route??

---

### Post by Dan Luevano on 2007-02-09
I personally haven't found a way to permanently remove the erraneous DEFAULT line in the router table, BUT...I have created a script that I cron to check and remove the line if it exists.  Here is the script...

root:~/scripts # cat checkroute.sh
#/bin/sh

rm -f /tmp/route-data.tmp /tmp/route.tmp
/sbin/route > /tmp/route-data.tmp 2>&1
if [ `cat /tmp/route-data.tmp | grep eth1 | grep default | wc -l` = "0" ]; then
#       exit 0
#       date > /tmp/route.tmp
#       echo -e "\n" >> /tmp/route.tmp
#       cat /tmp/route-data.tmp >> /tmp/route.tmp
#       echo -e "route tables ok" >>/tmp/route.tmp
        echo -e "`date` - route tables ok" >>/root/logs/route.log
#       mail -s "tviftp route data" [email]youremail@address.com[/email] < /tmp/route.tmp
#       rm -f /tmp/route.tmp /tmp/route-data.tmp
else
        date > /tmp/route.tmp
        echo -e "\n\n" >> /tmp/route.tmp
#       /sbin/route >> /tmp/route.tmp 2>&1
        cat /tmp/route-data.tmp >> /tmp/route.tmp
        echo -e "\nroute tables NOT ok, running route del command." >>/tmp/route.tmp
        echo -e "\n`date` - route tables NOT ok, running route del command." >>/root/logs/route.log
        echo -e "\nroute del -net default eth1\n\n" >>/tmp/route.tmp
        /sbin/route del -net default eth1 >>/tmp/route.tmp 2>&1
        /sbin/route >> /tmp/route.tmp 2>&1
        mail -s "tviftp route error" [email]youremail@address.com[/email] < /tmp/route.tmp
#       rm -f /tmp/route.tmp /tmp/route-data.tmp
fi
exit 0
root:~/scripts #


I run this every 15 minutes. That way if the DEFAULT line ever comes back (which it has) my script will remove it.

Hope this helps.

Dan Luevano

---

