---
title: "[SOLVED] Accessing Server services from internet"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by coops36 on 2008-03-15
I have installed Ubuntu 7 server edition as a LAMP server. I have also installed webmin, and ssh. The server has an internal IP 10.10.10.x and an external IP 195.86.244.x The problem is that I can access all the Services from any computer with a 10.10.10.x (my lan) and from any off the other external facing servers with a 195.86.244.x address. but I cannot access it from any other machine on the internet. I cannot even ping the ip. I have installed and reinstalled ubuntu LAMP in the past and never had this issue. I am a total newbie! 

I initially thought that it was an apache deny setting,but  all the services are unavailable (webmin and SSH). leaving me to believe it is a network card config error or setting.


Any tips or pointers much appreciated. MakoReactor I see you seem to have had the same issue...any resolution?


Dan

---

### Post by bsharp on 2008-03-15
Are your ports forwarded to the correct server?

---

### Post by ghost_ryder35 on 2008-03-15
What is the server using to get to the internet?  Make sure the ports are forwarded correctly and that any external firewall is configured correctly to let the correct ports through.  I belive SSH is 22.  You stated that you can not even ping the IP, sounds like the router/modem you are using has a built in firewall.

---

### Post by coops36 on 2008-03-15
The server is directly connected to the internet no port forwarding is required, VIA our ISP. I have had both a previous Ubuntu and windows webserver running on this IP. no problems

---

### Post by coops36 on 2008-03-15
Hi, there is no firewall, the server has been assigned one of the 10 external addresses provided to me by my isp. It seems that the server is only responding to requests on either the internal or external subnet and dropping everything else. 

Does ubuntu install with any firewall in place?

---

### Post by coops36 on 2008-03-15
Thanks for your time chaps(esses) The problem is fixed the issue was the Default route setting on the server where set to my LANs Gateway after I set this to the external router...BOOM...everything came on line. 

thanks Again

---

