---
title: "Trouble connecting to iNet"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by darkmage77 on 2007-05-25
Hello all,

This is my first time trying Ubuntu, and I have run into a problem after installation. I've got a dual-boot setup that looks like it went smoothly: I can log into both WinXP and Ubuntu Edgy. However, when I log into Ubuntu, my internet connection is not working properly. It is working in some fashion, as the update list is populated. However, Firefox will not connect, and I cannot install any of the updates.

I have a cable broadband connection, which I am running through a router on DHCP. It's a wired connection into an integrated ethernet port on my m-board, which has an nForce2 Ultra 400 chipset. WinXP is having no trouble connecting, as you can see. :p 

When I look at the network conf, it says that I have a loopback interface (l0) as well as my ethernet port (eth0). It's showing that eth0 is configured for DHCP. I've used Linux before (Mandriva), but I'm not secure enough in my knowledge to know how to get around.

If need be, I have a USB drive to port any drivers I might need into Ubuntu, but I'd like to think that there's a simpler solution that I just haven't found yet.

Any ideas?

---

### Post by Shazaam on 2007-05-25
How do you have your connection set up in Firefox?
"Preferences/General/Connection Settings"

---

### Post by wormser on 2007-05-25
Are you getting an IP address?  Have you tried pinging by domain name and ip address?  U se this IP 68.87.69.146.  Also try pinging your router and give us more details.  Here are the commands just in case.

**ifconfig**
**ping ipaddress**

---

### Post by darkmage77 on 2007-05-25
The problem resolved itself...sortof.

I'm in Ubuntu now, and I'm having a different problem. When I relogged into Edgy it initialized eth0 properly, so I grabbed the updates and restarted. But when I logged in after that, it didn't find my connection. So I restarted again, and it initialized properly. What I've seen since is that for every other login, it is not finding eth0. Is there any setting I can look at that might shed some light?

---

