---
title: "Shield's Up said I failed. Do I need a firewall?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-08-07
GRC Port Authority Report created on UTC: 2006-08-06 at 21:30:45

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    2 Ports Open
    0 Ports Closed
   24 Ports Stealth
---------------------
   26 Ports Tested

NO PORTS were found to be CLOSED.

Ports found to be OPEN were: 22, 80

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.




Solicited TCP Packets: RECEIVED (FAILED) 22,80 ports actively responded to our deliberate attempts to establish a connection

Unsolicited Packets: PASSED 

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet
===================================================

I am on a free access wifi hotspot should I install a firewall?

Thanks for your help.

---

### Post by _simon_ on 2006-08-07
Everyone should have a firewall!

---

### Post by tturrisi on 2006-08-07
> **orb9220 said:**
> 

I am on a free access wifi hotspot should I install a firewall?

Thanks for your help.

**No, you do NOT need a firewall**.  The AP-router is already using a firewall, at least it's likely using NAT.  Thus, your machine is protected.  ShieldsUp is scanning the AP-router, NOT your computer.  The AP-router has 2 open ports, port 80 (www) and port 22 (telnet).  These ports are used to configure the router.  Unfortunately, the AP-router is responding to ShieldsUp ping requests and it should be config'd to never respond to requests from the WAN.  However, it may be setup that way so the AP admin(s) can config the AP-router remotely.

Ubuntu default install does not have any open ports.  If YOU are running a telnet server & a www server, then yes, ports 80 & 22 may show as "open" on your comp IF you also config'd the AP-router to forward ports 80 & 22 requests to your isp adfdress, but if you did not install a www server & telnet service & did not do AP-router configs then you are secure.

As for security and wifi, well, there is NO such thing as secure wifi!  However, as the vast majority of wifi hotspot users will be running Windows, then you have little to worry about since **Windows wifi cards cannot capture the wifi traffic (other than their own)** and cannot even read ext2 & ext3 file systems used by linux (unless installed rare driver to do so).  So unless a fellow wifi user in the area is running linux and a wifi sniffer such as Kismet, then you are fairly safe and have nothing to worry about.

---

