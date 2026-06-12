---
title: "How do i tell? *need help fast*"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-08-26
How does one tell what ports they have open? like if they do not have access to the routers admin stuff, how do i tell what ports i are open so i can use VNC with my GF? like a program, or is it built into ubuntu or what?

LoL and the reason why i need help  fast is because i have a GF who does not have any comp experience and she has a short attention span for PC stuff.

---

### Post by Aiello on 2007-08-26
Well, if you don't have access to your router, good luck?

But anyways, there are a few sites out there that will send traffic to various ports to see if they are open, closed, or invisible. I will do some searching for you while I wait for some replies for my thread!:lolflag:

---

### Post by gundumfx on 2007-08-26
well in order for you to have t set a vnc you need to have acses to the rowetor do you

---

### Post by kellemes on 2007-08-26
[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by Aiello on 2007-08-26
Here is one where you put in the port you want to check: [http://www.canyouseeme.org/]("http://www.canyouseeme.org/")

---

### Post by dbott67 on 2007-08-26
What is it that you are trying to do exactly?  Are you trying to VNC to her computer?  If you are (and she is behind a router) you will need to have her forward port 5900 to her internal IP address.  If she does not have access to the router, you can always have her "reverse VNC" to you (but you will need to forward port 5500 on your router to your internal IP address).  

If neither of you have access to the router/firewall, then you will have to use an intermediate product such as "GoToMyPC" which is quite firewall-friendly, but requires that the PC you're connecting to be running Windows.  There's also NAT2NAT for UltraVNC (Windows only), which aids connections behind NAT routers (maybe it will run under wine?).

Take a look at my "HOWTO: Reverse VNC" below in my signature if you have access to your router/firewall.

If you could provide more information about the computers involved, network connection (behind NAT router; at work/school/home) and whether or not you have access to either router, we might be able to provide a better solution.

-Dave

---

### Post by wirelessmonkey on 2007-08-26
install nmap ... it's in the repositories.  Then run sudo nmap localhost.

---

### Post by ritterrav on 2007-08-26
> **wirelessmonkey said:**
> install nmap ... it's in the repositories.  Then run sudo nmap localhost.

will this automatically tell me any and all open ports of the router im currently behind?

---

### Post by wirelessmonkey on 2007-08-26
Well....sorta.  If you know the IP address of the router (should be easy enough) you can tell which ports are listening, and if you run a full scan, you can tell which ports are being filtered.  FYI there is a package called NmapFE that gives you a gui... make sure to start it from the command line ... sudo nmapfe.... so you get full functionailty.

---

### Post by finer recliner on 2007-08-26
sudo lsof -i

EDIT, sorry that doesnt list ports, just applications using internet

use nmap for port scanning.

---

