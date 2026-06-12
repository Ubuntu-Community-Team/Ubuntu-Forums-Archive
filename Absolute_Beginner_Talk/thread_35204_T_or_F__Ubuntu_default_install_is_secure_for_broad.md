---
title: "T or F:  Ubuntu default install is secure for broadband"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by snairofilac on 2005-05-18
If I have a cable modem, cable internet, no home network, and install the default ubuntu system with a fairly difficult password:  Is it secure, assuming i don't run damaging sudocode myself?

What modifications do you make on your system after install (or during) to make ubuntu more secure?

thanx

noobhelpers > noobhunters

---

### Post by dave9191 on 2005-05-18
It should be secure enough, but I would install a firewall like firestarter or configure IP tables myslef to make the PC invisable to the internet. Why take chances eh :)

---

### Post by snairofilac on 2005-05-18
my understanding is firestarter is frontend that configures iptables rules at startup?  

is firestarter the easiest/best way to configure iptables?

---

### Post by nocturn on 2005-05-18
It is secure enough (your password is not a big issue because there are no open services to the internet if you haven't installed any).

I always do recommend people to buy a cheap hardware router/fw though, they are not expensive and provide a good extra security layer (most have a built-in switch).

---

### Post by snairofilac on 2005-05-18
is the following accurate:

linux uses iptables as a filter for traffic into and out of the system.  it is a software firewall implementation.

hardware firewalls are more secure, and use proprietary firmware solutions to traffic filtering.

thanks for prompt replies

---

### Post by Burgundavia on 2005-05-18
Basically, there are no current Linux viruses in the wild. There have been, but they have mostly targetted servers.

Also, the Ubuntu default security policy is very good, probably the best in the Linux, if no the OS world.

Thus, you have no programs that "listen" to the world. 

That being said, if you want to secure your system further, a firewall is not a bad way to go.

Ok, more info:
1. Firestarter is a configuration tool for iptables. Run it once, and it tell the system to start your firewall everytime

2. The reason blackbox firewalls are safer on Windows machines is that until recently, windows had no firewall. This meant that after the networking was started, until the firewall started (when you logged in), your system is vunerable. This is not true on Linux machines, as the firewall should start before the network stack even starts up, leaving no gap in coverage.

3. A lot of the black-box routers you can buy for the home use iptables

4. Iptables is an enterprise-class firewall that many trust entire very highly secure systems to.

Hope this clears things up.

Corey

---

### Post by snairofilac on 2005-05-18
thank you for reply ...

<hd>[i]
3. A lot of the black-box routers you can buy for the home use iptables[/i]
 <hd>

do i understand correctly that i can buy a router at Walmart that has the same iptables implementation/protocol/whatchamacallit that my ubuntu desktop does?

<hd>
*4. Iptables is an enterprise-class firewall that many trust entire very highly secure systems to.*
 <hd>

what are the best resources for learning about iptables configuration on my ubuntu desktop?

---

### Post by az on 2005-05-18
"hardware firewalls are more secure, and use proprietary firmware solutions to traffic filtering."

No.


Out-of-the-box, Ubuntu is secure.  When you start installing packages from universe or elsewhere, it is up to you to ensure that you know what the package does so that you stay secure.

---

