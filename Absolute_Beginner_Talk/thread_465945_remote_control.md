---
title: "remote control"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by richard101 on 2007-06-06
Hi All

Ok, I'm happy with 6.06-desktop, and apache. Now I want to connect from work (windows xp) to make some pretty web-pages.

richard101

---

### Post by mlentink on 2007-06-06
Try RealVNC or TightVNC.  They operate pretty much in the same way as remote desktop on XP. The other way around it even is. Enable rdp on the XP box, and use the Terminal Server Client on your ubuntu box. 
I do it daily.
System>Preferences>Remote Desktop....

---

### Post by richard101 on 2007-06-06
great, thanks, do I want "VNC Free for Windows" or ~Linux(x86) ?

---

### Post by lazyart on 2007-06-06
For Windows since you're install it on XP.  But you'll need to enable remote sharing of the desktop in Ubuntu.

System>Administration(or maybe preferences)>Remote Desktop

Allow viewing and let remote user control desktop.  You'll have to forward port 5900 on your router to let traffic in.  And then you'll need a way to find your machine on the net-- dyndns.org is a way.

---

### Post by richard101 on 2007-06-07
Hi again

vnc doesnt seem to be working for me. When I put "http://oracle.podzone.org" into vnc-viewer it times out (Giving me no option to enter a password).

I did all the right things at home, with ubuntu,  IE: remote-desktop, and on the router forwarding port 5900 to static address 192.168.0.3. (I though about firestarter but in the end disabled it).

Please try my URL in vnc see if it times-out, perhaps there's a firewall issue at my work.

thanks

richard101

---

### Post by mlentink on 2007-06-07
I'm sorry, I should have given clearer instructions.

Here's how to do it.
1. Enable the VNC server by goint to System>Preferences>Remote Desktop (done)
2. In your router, enable port forwarding to port 5900 to the internal IP of your ubuntu-box (done)
3. Install a vnc viewer on your windows box (done)
4. In your vnc viewer, enter the ***external IP adress*** of your router. If you don't know this, run something like 'what is my ip' from your linux box, it should tell your this external adress


So it's not your URL that you want to connect to, but your external IP adress, i.e. the IP adress your router got from your ISP. If this changes very often, I would recommend subscribing to a dynamic IP setup like dyndns

Hope this helps!

---

### Post by richard101 on 2007-06-07
thanks. not sure i fully understand.

my isp gives me a dynamic ip-address, i've a page on dyndns that, i guess,  knows that changable ip-address and assigns it to a static url.

fyi - my page in dyndns looks like this ...

"Modify Dynamic DNS oracle.podzone.org
IP in Database/DNS: 90.199.59.140  
Last Updated: May 16, 2007 2:11:56 PM"
...

---

### Post by mlentink on 2007-06-07
> **richard101 said:**
> IP in Database/DNS: 90.199.59.140  


Then it would seem you need to use 90.199.59.140.
BTW I saw an update date of a few weeks ago. Does your ISP change IP adresses only once a month or so? In that case, I would personally use your current ISP-IP and not bother with DynDNS at all. Or do you run a mailserver or webserver that needs to be available without IP?

---

### Post by richard101 on 2007-06-07
Im hoping to run a web-server once I get these fiddly bits sorted.

perhaps i'm behind a firewall here that blocks 5900

does it time out when you use vnc-viewer with 90.199.59.140 ?
(or do you get a password dialogue box?)

---

### Post by richard101 on 2007-06-07
definately getting there now :-)

First I did the whatsmyip from my ubuntu-machine, and its different from the dyndns one i saw earlier - i guess perhaps there web-page is out-of-date.

next, connected from my home XP machine (using internal ip-address) and found out I had inadvertently ticked the ask-local-user-for-permission box (or whatever it is).

...

---

### Post by Ek0nomik on 2007-06-07
So, what problem are you still having?

---

### Post by richard101 on 2007-06-07
possibly none, cannot test remotely, until tomorrow.

---

### Post by Ek0nomik on 2007-06-07
> **richard101 said:**
> possibly none, cannot test remotely, until tomorrow.

Post in the thread if you have more problems.  :)  I have some VNC experience under my belt.

---

### Post by dale3h on 2007-06-08
If you do continue to have problems, try Hamachi. It's a Lord in the VPN world. So easy to use, so easy to install, and a very small program. Take up very little memory and disk space. :)

On top of how easy it is, it allows you to 256-bit secure your connection. Any data transmitted over the Hamachi adapter is totally secure.

Here's an easy install guide for Hamachi: [http://doc.gwos.org/index.php/VNC_and_Hamachi](http://doc.gwos.org/index.php/VNC_and_Hamachi)

---

