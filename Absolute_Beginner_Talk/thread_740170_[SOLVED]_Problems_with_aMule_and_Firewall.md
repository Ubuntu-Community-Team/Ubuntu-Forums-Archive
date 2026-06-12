---
title: "[SOLVED] Problems with aMule and Firewall"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by amandalia47 on 2008-03-30
Ok guys I know this question has been asked to death, because I have been searching the forum for a while but I have still not found an answer to my question.

I just started using aMule I cannot get Kad to be "un-Firewalled!"  My globe icon has a green upload arrow and a yellow download arrow.  Kad is firewalled when I first start aMule and becomes Off after a while.  

I have a router which I set up myself.  I have set port forwarding in many different ways and none of them work.  I have tried setting 3 different rules as follows:

4662 TCP Enabled
4672 UDP Enabled
4665 UDP Enabled

I have also tried:

4662-4672 Both Enabled
4665 UDP Enabled

and I have tried both of these with 4665 UDP Enabled and Disabled because I read on different FAQ's that if your router uses NAT you should disable this port and I do not know if my router uses NAT or not.

I have a Linksys Wireless-G router.  I must also mention that when I used Azureus with Windows, I was able to set up port forwarding and it worked perfectly fine the first time.  

I have read many of the threads here and most mention iptables and I have tried that, but I get the same error every time:

iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

I also cannot figure out how to log in as root.... I have tried and it's really bugging me that I can't, but usually I am just asked to enter a password but iptables does not ask.

I DO NOT HAVE A FIREWALL.  My router does not enable a firewall and I have not downloaded one and I have searched my whole system and have not found one either.

If you need more information I'll be happy to give it, any advice at all is appreciated.

Thanks

---

### Post by MeTylerDurden on 2008-03-30
I am going to wait for the newer version of amule because I had my ports set up just like you mentioned  and still was problematic..       i tried for about 4 hours or so and finally had to admit that there was no magical answer with amule  ..    but to wait.     (yeah i wanna be root 2):popcorn:  

/The Liberator who destroyed my property has realigned my perception

---

### Post by Hallvor on 2008-03-30
You must write sudo in front of your command since it requires root:  

```
sudo iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
```

---

### Post by Hallvor on 2008-03-30
> **MeTylerDurden said:**
> I am going to wait for the newer version of amule because I had my ports set up just like you mentioned  and still was problematic..       i tried for about 4 hours or so and finally had to admit that there was no magical answer with amule  ..    but to wait.     (yeah i wanna be root 2):popcorn:  

/The Liberator who destroyed my property has realigned my perception

Just download a .deb from amule.org and try it out if you need the newest version.

---

### Post by amandalia47 on 2008-03-30
Thanks Hallvor, it seemed to work just fine using sudo... except that aMule is still firewalled.  Perhaps I have been given wrong iptable information.... this is what I typed: 

sudo iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 4661 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4662:4665 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4672 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4675 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 4662 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 4661 -j ACCEPT
sudo iptables -A OUTPUT -p udp --dport 4662:4665 -j ACCEPT
sudo iptables -A OUTPUT -p udp --dport 4672 -j ACCEPT
sudo iptables -A OUTPUT -p udp --dport 4675 -j ACCEPT

I do not know if these are right or not, but it was the most complete one I found.  I will keep looking for other iptables information.

---

### Post by annda on 2008-03-30
i had to do this too a while ago: go to networks and in the kad tab hit bootstrap from known clients. this may take a while. if it doesn't work, try connecting to another server. repeat.

---

### Post by amandalia47 on 2008-03-30
Annda... you are so awesome!  It worked right away and was so easy!

Thank you very much!!

---

