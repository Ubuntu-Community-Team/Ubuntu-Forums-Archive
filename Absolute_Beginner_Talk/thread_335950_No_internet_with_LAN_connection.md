---
title: "No internet with LAN connection"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by joby on 2007-01-11
I just installed the latest version of ubuntu but cannot get the internet to work. I've seen similar problems on the forums but there a some differences and couldnt understand the advice (mainly becuase i dont use a router). I use a Cat 5e to connect to my Windows Xp computer which has cable modem. Does the XP make a difference at all? I tried setting up a network on xp and pinged the listed ip from the ubuntu computer and it worked... so it recognizes its there but still no internet. Any help? thanks in advance.

---

### Post by flexible on 2007-01-11
Have you tried to input values for IP, subnet mask and DNS server (As appears in windows XP LAN properties) into Ubuntu? Are you using any firewall in Ubuntu?

---

### Post by joby on 2007-01-12
Sorry bout the delay but some other problems came up... tried changing the setting in ubuntu from DHCP to static with an IP address similar to the one listed on the LAN connection. I tried putting in the IP of the computer with internet as the gateway but it still wont work. I even tried putting the IP addresses of the internet connection as the gateways still nothing.

---

### Post by medley on 2007-01-12
> **joby said:**
> Sorry bout the delay but some other problems came up... tried changing the setting in ubuntu from DHCP to static with an IP address similar to the one listed on the LAN connection. I tried putting in the IP of the computer with internet as the gateway but it still wont work. I even tried putting the IP addresses of the internet connection as the gateways still nothing.

You've probably already checked this, and maybe you're already sharing with some other Windows boxes, but if not, make sure you have Internet Sharing enabled on the Windows machine attached to the modem.

Phil

---

### Post by joby on 2007-01-12
yeah. thats done. still no net.

---

### Post by joby on 2007-01-12
Can someone tell me if this relates to me?
> **HereInOz said:**
> Sounds like your ubuntu machine is not picking up its DNS from the router.  Go in to System > Administration > Networking and try setting a static IP address in the same subnet as the router's internal IP address, set your gateway as the router's internal IP address and enter the DNS addresses of your ISP in the DNS section of the Networking properties box, and I reckon you will be there.

 As a test, try pinging 66.102.7.104   

If you can ping that, try pinging [www.google.com](www.google.com) 

If you can't ping that, then it is a DNS problem and the above process will probably fix it.

I can ping 66.102.7.104 but not [www.google.com](www.google.com) but i dont use a router does this mean i have DNS problem? cos i have no idea what to do if i do.

---

### Post by medley on 2007-01-14
> **joby said:**
> Can someone tell me if this relates to me?


I can ping 66.102.7.104 but not [www.google.com](www.google.com) but i dont use a router does this mean i have DNS problem? cos i have no idea what to do if i do.

Sounds like a DNS problem to me. You could try manually entering the DNS host IP(s) that your Windows machine uses into your Linux n/w configuration. I don't know how to tell you to do it as I don't know what desktop you're using. In KDE you can find in Internet & Network/network settings under the dns tab. You can find out what your Windows system is using for DNS by typing 'ipconfig -all' at a command prompt on that box. Write down the IP addresses for the dns server(s) and use those.

Also try entering "http://66.102.7.104" at your browser's address bar and if you go to google, your linux box doesn't know where to find a dns server and the above will fix you up.

---

