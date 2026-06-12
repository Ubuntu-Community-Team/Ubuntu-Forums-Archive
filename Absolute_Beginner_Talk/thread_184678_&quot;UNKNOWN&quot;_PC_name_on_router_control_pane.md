---
title: "&quot;UNKNOWN&quot; PC name on router control panel"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Pugaciov on 2006-05-30
Is it normal that on the Netgear (DG834GT) router setup, on "Attached Devices" my PC (first LAN port, 192.168.0.2) is displayed as "UNKNOWN"?

Thanks

Cheers

---

### Post by Clunsford on 2006-05-30
I think you can fix that when you create a samba server and assign your NT name or somthing like that i can't really remember.

Don't worry about it though it won't hurt nothing; Those home use routers'n such suck when it comes to customability and working with things that don't fit into the specific paramater of their intent...   (try to get a sony location free player to work with em)

---

### Post by nanotube on 2006-05-30
that is normal, because ubuntu doesn't by default send a name to the router. if you want to change it, edit file /etc/dhcp3/dhclient.conf and find the line that looks like
```
#send host-name "andare.fugue.com";
```
and uncomment it, and change the andare.bla stuff to the name you want it to have.

---

### Post by bruce89 on 2006-05-30
I think it's usually the same as the hostname.

---

### Post by Pugaciov on 2006-05-30
[QUOTE=nanotube]that is normal, because ubuntu doesn't by default send a name to the router. if you want to change it, edit file /etc/dhcp3/dhclient.conf and find the line that looks like
```
#send host-name "andare.fugue.com";
```
and uncomment it, and change the andare.bla stuff to the name you want it to have.[/QUOTE]

Uncomment means to delete the # before the line right?

Thanks

---

### Post by nanotube on 2006-05-30
[QUOTE=Pugaciov]Uncomment means to delete the # before the line right?

Thanks[/QUOTE]
right :)

---

### Post by Pugaciov on 2006-05-30
[QUOTE=nanotube]right :)[/QUOTE]

I've modified the line, but it doesn't seem to work.

---

### Post by IainT on 2006-05-30
Have you restarted your router since making the change? Mine requires me to restart it to effect any slight changes.

---

### Post by Pugaciov on 2006-05-30
[QUOTE=IainT]Have you restarted your router since making the change? Mine requires me to restart it to effect any slight changes.[/QUOTE]

No, actually I didn't restart it. I'll try as soon as possible (aMule is working :p).

Thanks again.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=Pugaciov]No, actually I didn't restart it. I'll try as soon as possible (aMule is working :p).

Thanks again.[/QUOTE]

I restarted but It doesn't work, I still have "UNKNOWN"...

---

### Post by nanotube on 2006-05-31
[QUOTE=Pugaciov]I restarted but It doesn't work, I still have "UNKNOWN"...[/QUOTE]
you gotta restart your comp, so that dhclient reads its new config file.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=nanotube]you gotta restart your comp, so that dhclient reads its new config file.[/QUOTE]

Yes, I restarted it, but nothing...

---

### Post by nanotube on 2006-05-31
[QUOTE=Pugaciov]Yes, I restarted it, but nothing...[/QUOTE]
hm, strange. post your dhclient.conf file here, i can see if maybe you made a typo... other than that, i am not sure what else to do.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=nanotube]hm, strange. post your dhclient.conf file here, i can see if maybe you made a typo... other than that, i am not sure what else to do.[/QUOTE]

```
send host-name "Hatch"
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by nanotube on 2006-05-31
aha! (well, maybe)
you forgot the semicolon at the end of your send host-name line. it should be
```
send host-name "Hatch";
```
try that.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=nanotube]aha! (well, maybe)
you forgot the semicolon at the end of your send host-name line. it should be
```
send host-name "Hatch";
```
try that.[/QUOTE]

Tried. It keeps saying "UNKNOWN".
Maybe it should be written uppercase?

---

### Post by nanotube on 2006-05-31
[QUOTE=Pugaciov]Tried. It keeps saying "UNKNOWN".
Maybe it should be written uppercase?[/QUOTE]
by tried you mean, you put that it, and then rebooted router, and your computer? if so... then hmm, i am out of ideas. 

the upper/lower case shouldn't really make a difference, but hey, i dont suppose it could hurt. try it all uppercase, and all lowercase, and see if anything bites.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=nanotube]by tried you mean, you put that it, and then rebooted router, and your computer? if so... then hmm, i am out of ideas. [/quote]

Yup.

[QUOTE=nanotube]
the upper/lower case shouldn't really make a difference, but hey, i dont suppose it could hurt. try it all uppercase, and all lowercase, and see if anything bites.[/QUOTE]

Ok this will be next step then :)

---

