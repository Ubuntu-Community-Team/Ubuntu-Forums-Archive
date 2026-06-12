---
title: "Where is DHCP information stored?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by glave on 2006-11-21
Running ifconfig gives me some information, but its not showing me what I'm looking for, like what wins server did dhcp assign, what dns, lease time, etc.

Where would this info be stored at?

---

### Post by Dasold on 2006-11-21
according to the man page of dhclient the info is saved here:
**/var/lib/dhcp/dhclient.leases**
I cannot test it 'cos I have static ips on my lan ;)

---

### Post by biffta on 2006-11-21
Dont think this is exactly what you want but may be a step in the right direction:
Alt+f2 then type network-admin

---

### Post by biffta on 2006-11-21
> **Dasold said:**
> according to the man page of dhclient the info is saved here:
**/var/lib/dhcp/dhclient.leases**
I cannot test it 'cos I have static ips on my lan ;)

Its called /var/lib/dhcp3 on mine, but unfortunately it contains only blank files :-k (I am on dhcp):

davidh@hop:~$ ls -l /var/lib/dhcp3
total 0
-rw-r--r-- 1 dhcp root 0 2006-11-15 21:26 dhclient.ath0.leases
-rw-r--r-- 1 dhcp root 0 2006-11-15 21:26 dhclient.eth1.leases
-rw-r--r-- 1 dhcp root 0 2006-11-15 21:26 dhclient.eth2.leases
-rw-r--r-- 1 root root 0 2006-10-25 14:27 dhclient.leases
-rw-r--r-- 1 dhcp root 0 2006-11-15 21:26 dhclient.wlan0.leases

---

### Post by glave on 2006-11-21
Yea, I found that directory of leases, but mine are the same, all 0 byte files. Cat on all of them shows nothing. 

Network-admin only shows me pretty much exactly what ifconfig does (actually less). No information about lease time, assigned servers or anything.

---

### Post by maximouse on 2006-11-21
> **glave said:**
> Where would this info be stored at?

/var/lib/dhcp3/dhclient.eth0.leases for eth0.

---

### Post by civic_si on 2006-11-21
My machine is static so i cant tell if there is a difference but try 

cat /etc/network/interfaces

that shows the address mask and gateway on my card.
i dont think that this will show you the DNS. DNS entries are showed in the /etc/resolv.con file.

---

### Post by glave on 2006-11-21
/etc/network/interfaces  shows what interfaces there are, but no information at all about them.

And everything in /var/lib/dhcp3/ is a 0 byte file which cats to nothing. ](*,)

---

### Post by Dasold on 2006-11-21
OK, I think I finally found the answer...
try: **sudo dhclient eth0**

and you should get something like that:
```

Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from x.x.x.x
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from x.x.x.x
bound to x.x.x.x -- renewal in 3586 seconds.

```

---

### Post by glave on 2006-11-21
Ok, that got me my lease time, but anyway to see if I'm being assigned a WINS server?

---

### Post by maximouse on 2006-11-21
you can use "sudo dhclient -lf leases.txt", and then "less leases.txt".

---

### Post by glave on 2006-11-22
I'm guessing that 

 option netbios-name-servers 192.168.168.11;

would be the WINS server then?

If so, viola! I can't believe this info isn't in a flat file somewhere though!

---

### Post by biffta on 2006-11-23
> **glave said:**
> I'm guessing that 

 option netbios-name-servers 192.168.168.11;

would be the WINS server then?

If so, viola! I can't believe this info isn't in a flat file somewhere though!

Flatfile? This information should all be in the network-admin graphical tool. But I guess that's more a gnome issue than Ubuntu.:-k

---

