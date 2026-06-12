---
title: "[SOLVED] Setup question on Dial-Up sharing"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Silvain on 2008-01-06
Some advice please.
Checked my ethernet connect with ping, Can ping the address 192.168.0.1 from the  2nd machine at 192.168.0.4 fine. And ping machine at 192.168.0.1 fine with machine at 192.168.0.4 so my network seems to be intact.

Am trying to share a Dial-Up connect made by a Ubuntu system, over Ethernet card. Heres the commands I ran.
```

root@silvain-desktop:/home/silvain# ifconfig eth1 192.168.0.1
root@silvain-desktop:/home/silvain# iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE 
root@silvain-desktop:/home/silvain# echo 1 > /proc/sys/net/ipv4/ip_forward
root@silvain-desktop:/home/silvain# /etc/init.d/dnsmasq restart
Restarting DNS forwarder and DHCP server: dnsmasq.
root@silvain-desktop:/home/silvain# dpkg-reconfigure ipmasq
root@silvain-desktop:/home/silvain# gedit /etc/sysctl.conf
```

I am suspecting that on the line where entered commands went

"iptables -t nat -A POSTROUTING -o eth1 -j "

that instead of eth1, I should have typed ppp0 ? My system at 192.168.0.4 cant see internet at all right now. What should I try next ?

---

### Post by Silvain on 2008-01-07
Ok gave up on that prior setup, am trying again based on info at :

[https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

Here is what have done on my "sharing internet" machine so far.

```
root@silvain-desktop:/home/silvain# iptables -A FORWARD -i eth1 -o ppp0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
root@silvain-desktop:/home/silvain# iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
root@silvain-desktop:/home/silvain# iptables -A POSTROUTING -t nat -j MASQUERADE 
root@silvain-desktop:/home/silvain# sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
 
```

Also did the bit where have to add the two lines to my  /etc/sysctl.conf file, since am running Gutsy here.

Next went to do the client machines part. But on the part where it says > Add gateways, ask the server maintainer for the DNS and include then on /etc/resolv.conf such as:
My Dial-up Isp has DNS servers ,

Here is all i see in that /etc/resolv.conf file on my client machine: ```
 :domain Home
```

What should I add here? Wondering how to transfer this info to my client systems, What to do next ?

---

### Post by Silvain on 2008-01-07
update, gave up on that one also. Just found this [http://ubuntuforums.org/showthread.php?t=111972]("http://ubuntuforums.org/showthread.php?t=111972")

---

### Post by Silvain on 2008-01-07
Ok got my DHCP server up with infos from this site. :[http://www.howtoforge.com/dhcp_server_linux_debian_sarge]("http://www.howtoforge.com/dhcp_server_linux_debian_sarge")

Trying to setup the script part now.

---

### Post by Silvain on 2008-01-08
The last thing that was necessary to make my setup work was, enabling my modem, navigate to  "System"->"Administration"->"Network"_-> enter root pass, then had to setup my "Modems connection" entries And then tic the box beside the "Modem connection". This allows the modem to dial on booting, This seems to be very important, as connecting later by manually starting the connect did not work for me.

Hope this might help someone else, sure had to go "Jump" some here!
Silv

---

