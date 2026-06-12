---
title: "Static IP"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by reala on 2008-03-20
Hi,

I'm running Ubuntu 7.10 and i'm having issues setting up a static ip so i can use port forwarding with utorrent via wine.

I've tried following guides online and the forum hints above but they are not working for me or realistically i am not understanding what to do. Under windows XP i had no issue setting  up a static IP and configuing it in my router for bittorrent on the port 57151


My /etc/network/interfaces only says

auto lo
iface lo inet loopback

I don't have any idea what a loopback interface is, i know eth0 is my network card correct ?

All i want to do is give my ubuntu machine a static ip of 192.168.1.150 and then set up port forwarding to that in my router settings ( i can manage that myself surprise surprise).

So far i've gone to System/Admin/Network and then Wired Connections, Properties.disable roaming mode and then set it to static

IP 192.168.1.100
subnet 255.255.255.0
gateway 192.168.1.1

i am still getting the unconnectable icon in utorrent and portforward.com reports

Checking port 57151 on 123.243.104.135...

Error! Port 57151 does not appear to be open.

Any help would be much appreciated.

---

### Post by adult swim on 2008-03-20
so you have gone through and opened port 57151 in your router?  do you have an exception for port 57151 in your firewall?

---

### Post by kpkeerthi on 2008-03-20
Do you have firestarter running? You need to open up the port in firestarter also.

What does the below command print?
```

sudo /etc/init.d/firestarter status

```

---

### Post by reala on 2008-03-20
Yes, port 57151 is open on my router.

I downloaded Firestarter earlier and installed it. This is the response i get.

reala@reala:~$ sudo /etc/init.d/firestarter status
[sudo] password for reala:
 * Firestarter is running...
reala@reala:~$

---

### Post by sayakb on 2008-03-20
Click on the nm applet icon and click on Manual Configuration. Open the Properties for the Wired Connection, then Uncheck roaming mode and select Static IP Address at the Configuration drop-down menu. Add your IP, Subnet and gateway there.

---

### Post by reala on 2008-03-20
> **LinuxIsInnovation said:**
> Click on the nm applet icon and click on Manual Configuration. Open the Properties for the Wired Connection, then Uncheck roaming mode and select Static IP Address at the Configuration drop-down menu. Add your IP, Subnet and gateway there.

I've done this and i can ping 192.168.1.100 no problems but it's still no go with utorrent in wine or port forwarding. It's the same machine that was set up on the same port for utorrent in windows with the same static ip and it worked fine.

I've also just tried setting up a new IP address and added the same information to my router but i'm still having the same issue.

---

### Post by kpkeerthi on 2008-03-20
> **reala said:**
> Yes, port 57151 is open on my router.

I downloaded Firestarter earlier and installed it. This is the response i get.

reala@reala:~$ sudo /etc/init.d/firestarter status
[sudo] password for reala:
 * Firestarter is running...
reala@reala:~$

By default firestarter blocks are incoming traffic. You need to open Port 57151 in firestarter.
1. System -> Admin -> Firestarter -> Policy Tab
2. Select In-bound traffic policy (if not selected already)
3. Right click where it says **Allow service | Port | For** and then select add rule and fill in the port information as needed.
4. To be sure restart firestarter
```
/etc/init.d/firestarter stop
/etc/init.d/firestarter start

```

Now scan your port.

---

### Post by reala on 2008-03-20
Did that but i'm still unconnectable.

It seems so simple yet it's killing me.

---

### Post by kpkeerthi on 2008-03-20
Did you restart your router after configuring port forward? I'm not sure but this was required for **me**.

---

### Post by reala on 2008-03-20
No i've never needed to do that in the past but i will reset it now.

This is what i have

[http://img87.imageshack.us/img87/4808/screenshot1qj3.png](http://img87.imageshack.us/img87/4808/screenshot1qj3.png)

---

### Post by reala on 2008-03-20
Reboot of router and pc has it all working fine now.

Thanks for the help, rather big learning curve for myself but i'm feeling enthusiastic about my PC for the first time in a long time using ubuntu !

---

### Post by adult swim on 2008-03-20
snatch those torrents!

---

### Post by kpkeerthi on 2008-03-20
> **reala said:**
> Reboot of router and pc has it all working fine now.

Thanks for the help, rather big learning curve for myself but i'm feeling enthusiastic about my PC for the first time in a long time using ubuntu !

Glad it worked for you. Sometimes the " **windows mantra** " does work for linux. LOL :)

---

