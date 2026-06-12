---
title: "How do I change my IP?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-01
How would I go about changing my IP address? I already tried 

/etc/init.d/networking restart


Didn't work.

---

### Post by coffeecat on 2006-10-01
Use the GUI. In Gnome try System > Administration > Networking.

---

### Post by voodoonirvana on 2006-10-01
Do I just deactivate and then ativate the connection?

---

### Post by simohell on 2006-10-01
Well it depends on how you got your IP address in the first place:

1) did you set it manually or
2) get in automatically

1) You can change your IP address by editing /etc/networking/interfaces file,
if you have a static IP you can change it (hope it does not conflict with another computer) and restart networking.

2) Usually a DHCP server gives the same computer the same IP address based on  MAC id of the network card. (If there are more connections tha available IPs then its a bit different.)

If you have access to the DHCP server you can probably work something out.

If not, it might be your best shot to simply replace your network card. If it is integrated, you can of course put in an additional card.

In some cases (quite often actually) your computers IP is not the IP that is shown in the internet. To change that IP you would need get access to your router. In some cases you probaly would even need to have access to your ISP's system.

Maybe more confusing than helpful, but in general some times it is quite easy and sometimes it is rather impossible. Depends on your situation...

---

### Post by voodoonirvana on 2006-10-01
> **simohell said:**
> Well it depends on how you got your IP address in the first place:

1) did you set it manually or
2) get in automatically

1) You can change your IP address by editing /etc/networking/interfaces file,
if you have a static IP you can change it (hope it does not conflict with another computer) and restart networking.

2) Usually a DHCP server gives the same computer the same IP address based on  MAC id of the network card. (If there are more connections tha available IPs then its a bit different.)

If you have access to the DHCP server you can probably work something out.

If not, it might be your best shot to simply replace your network card. If it is integrated, you can of course put in an additional card.

In some cases (quite often actually) your computers IP is not the IP that is shown in the internet. To change that IP you would need get access to your router. In some cases you probaly would even need to have access to your ISP's system.

Maybe more confusing than helpful, but in general some times it is quite easy and sometimes it is rather impossible. Depends on your situation...

Yeah I know what you mean, Im trying to change the one that the internet sees. And i am using DHCP on a router.

---

### Post by coffeecat on 2006-10-01
> **voodoonirvana said:**
> Im trying to change the one that the internet sees.

Then you'll have to talk to your ISP. Your system can't change that.

---

### Post by sbergman27 on 2006-10-01
Either request a change from your ISP or replace the router.  Your public IP typically depends upon the MAC address of the interface issuing the DHCP request.  When it changes the IP address will change.

---

### Post by Fass on 2006-10-01
> **sbergman27 said:**
> Either request a change from your ISP or replace the router.  Your public IP typically depends upon the MAC address of the interface issuing the DHCP request.  When it changes the IP address will change.

The thing being that many routers allow you to clone MACs, meaning you can switch the MAC yourself...

---

### Post by coffeecat on 2006-10-01
Or just switch the modem/router off and on occasionally. If you haven't got a fixed IP address contract, more than likely you'll be allocated a different address each time you reconnect. That certainly happens with my ISP.

---

### Post by sbergman27 on 2006-10-01
> The thing being that many routers allow you to clone MACs, meaning you can switch the MAC yourself...

Fass,

Yes, but I don't do that myself and I don't recommend it to others on gerneral principle.

> If you haven't got a fixed IP address contract, more than likely you'll be allocated a different address each time you reconnect.

coffeecat,

That depends upon your ISP.

In general, I find that:

1. Dial up always assigns new addresses.
2. xDSL usually assigns new addresses.
3. Cable usually does *not* assign a new address unless the MAC address changes.

YMMV.

-Steve

---

### Post by NetworkGuy on 2006-10-01
Are you having a problem with an application that requires changing your public IP address?

---

### Post by Fass on 2006-10-01
> **sbergman27 said:**
> Fass,

Yes, but I don't do that myself and I don't recommend it to others on gerneral principle.

I just think it's a bit drastic to tell someone to buy a new router when something as trivial as changing the MAC on the one he already has can work just as well. 

This is, of course, unless his ISP binds IPs and access to MACs (not that unusual where I live, hence the need for routers to be able to clone MACs in the first place.)

---

### Post by sbergman27 on 2006-10-01
> **Fass said:**
> I just think it's a bit drastic to tell someone to buy a new router when something as trivial as changing the MAC on the one he already has can work just as well.

That's why I started out by recommending that he request an IP address change from his ISP rather than resorting to MAC address trickery. ;-)

---

### Post by Fass on 2006-10-01
> **sbergman27 said:**
> That's why I started out by recommending that he request an IP address change from his ISP rather than resorting to MAC address trickery. ;-)

Trickery - at least there is nothing underhanded about it, and will be a lot quicker than waiting for the ISP to probably say no. :D

---

