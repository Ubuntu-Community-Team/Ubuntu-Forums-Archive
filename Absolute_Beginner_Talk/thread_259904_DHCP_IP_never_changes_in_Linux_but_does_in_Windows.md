---
title: "DHCP IP never changes in Linux but does in Windows"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by sleepingsmile on 2006-09-18
I'm a newbie, I have Ubuntu Dapper running and in Gnome everything just worked as far as my high speed cable modem connection goes but with one problem:

My IP should be dynamic, when I boot into WinXP it changes to a different IP address, but within Ubuntu the IP address is the same every time and has been since I installed Dapper when it was released.

Why does the IP address change when I boot into WinXP (as it should because it's dynamic) but not in Ubuntu? I'm using the default settings for Ubuntu Dapper Linux and haven't modified anything as far as networking goes.

Can someone please help me?

I can use the internet with Ubuntu Dapper but I don't feel that it's correct to have the same IP address for months and it never changes every time I boot into Ubuntu Dapper to use the internet, but it changes when I boot into WinXP, something is not right here?

My hostname is always my username like this: username-desktop
Could that have something to do with it? I know nothing about networking so please answer with gentle information... thank you

---

### Post by Najand on 2006-09-18
Well, for dynamic DHCP IP Addresses it is more normal NOT to change it after a boot up.... The problem is not with Ubuntu , but with your windows I think. The server with DHCP abilities usually must remember your MAC address and give the same IP address the next time you use that server again...

---

### Post by sleepingsmile on 2006-09-18
> **Najand said:**
> Well, for dynamic DHCP IP Addresses it is more normal NOT to change it after a boot up.... The problem is not with Ubuntu , but with your windows I think.

I turn on the PC in the morning and turn it off in the evening so the computer is off almost every night for hours and for **months** through this cycle the IP in Ubuntu is the same, **it (the IP) has never changed, how can that be dynamic?**

When I boot back into Ubuntu it still has the same IP (the IP it had before I went into WinXP) but it had changed when I went into WinXP, not so in Ubuntu it still goes to the same IP it has had for months and has never changed.

This is a problem isn't it?

---

### Post by Najand on 2006-09-18
Well, You are expecting everytime, on a network with 1000 people on it turn on and off they computers every IP addresses change? Then Administrating such a server is much more difficult than giving static IP addresses to everyone of the people on that server. It is dynamic, because there is no need to set up IP address on every computers on the network and when there is lack of IP addresses, then server will give the IP addresses of those computers who are not active on the network to those who are active... But this rarely happens...

---

### Post by sleepingsmile on 2006-09-18
> **Najand said:**
> Well, You are expecting everytime, on a network with 1000 people on it turn on and off they computers every IP addresses change? Then Administrating such a server is much more difficult than giving static IP addresses to everyone of the people on that server. It is dynamic, because there is no need to set up IP address on every computers on the network and when there is lack of IP addresses, then server will give the IP addresses of those computers who are not active on the network to those who are active... But this rarely happens...

So this is not a problem then?

Why am I being assigned the same IP address for months when I boot into Ubuntu?

Does this have to do with my unique hostname of username-desktop ?

I thank you for your help I do not know much about networking and you are helping me fast and friendly it is very nice.

---

### Post by Najand on 2006-09-18
It might change sometimes, but not always... And it does not have to do with your hostname.... Because hostname is simply your local hostname (in other words, your computer name). I am administrating a server in the university. Whenever I configure the DHCP data, some of the IP addresses changes and some doesn't... So don't worry... There is no problem using the same IP address all the time... Well, I am still using the Static IP address I bought, a couple of years ago and does not have any problem with it at home.

---

### Post by sleepingsmile on 2006-09-18
> **Najand said:**
> It might change sometimes, but not always... And it does not have to do with your hostname.... Because hostname is simply your local hostname (in other words, your computer name). I am administrating a server in the university. Whenever I configure the DHCP data, some of the IP addresses changes and some doesn't... So don't worry... There is no problem using the same IP address all the time... Well, I am still using the Static IP address I bought, a couple of years ago and does not have any problem with it at home.

Thank you I am learning from your information.

If it does not have to do with my hostname, how is it that my IP address is the same since I installed Ubuntu but it changes in Windows every time? Why does it just change back to the same IP address in Ubuntu every time? That is what I do not understand, but maybe you have answered this and I don't see it so I chase my own tail like a dog for awhile while I try to understand this.

Thank you for helping me, one other thing, in the Firestarter firewall, I have no router, I use Firestarter, do I block broadcast external and internal or one or the other ? I allow two  192 addresses one is something like 192.168.100.1 and the other is similar to that is that okay to allow otherwise I see port 68 and 67 floods in my event log

edit to add - I don't have 192.168.100.1 and the other 192 address into my /etc/hosts file because the hosts file changes every time I boot Ubuntu so it just has the localhost and username-desktop entries is this okay or do I worry about spoofing attacks

---

### Post by muep on 2006-09-18
I, too, have a dynamic IP address that hasn't changed in months. It is normal. I don't know about Windows though, haven't used it in ages...

---

### Post by sleepingsmile on 2006-09-18
> **muep said:**
> I, too, have a dynamic IP address that hasn't changed in months. It is normal. I don't know about Windows though, haven't used it in ages...

another fast reply thank you for the information I won't be troubled by this behaviour in Ubuntu now since two people say this is the way it is.... I await reply for Firestarter help and that will be all for now.. oh but one other thing in addition to my Firestarter questions above.. is there a way to force a new IP request since it's dynamic just to see if I may get a new IP since it's dynamic or is this not nessessary?

---

### Post by Najand on 2006-09-18
There might be different reasons... Err... Like a timeout error which makes RSA server to send a different IP address to the user on the network... You are using internet just fine, right? I don't think there is any problem with that unless you want to login to your machine using ssh and changing IP address all the time, makes difficulties...

---

### Post by sleepingsmile on 2006-09-18
> **Najand said:**
> There might be different reasons... Err... Like a timeout error which makes RSA server to send a different IP address to the user on the network... You are using internet just fine, right? I don't think there is any problem with that unless you want to login to your machine using ssh and changing IP address all the time, makes difficulties...

Yes I use internet fine but I notice in Ubuntu it drops connection once per day but in Windows it does not drop connection, thank you for helping me you have helped me greatly now I just need the firestarter questions answered and I will be on my way =D>

edit to add - do I need to install and configure dhcpd? I have dhcp only installed, I do not have additional computers on the cable modem ethernet connection only one I am using but I don't know much about all of this

ok this is what I am wondering too about firestarter:

In the Firestarter firewall (I have no router, I use Firestarter) do I block broadcast external and internal or one or the other ? I allow two 192 addresses one is something like 192.168.100.1 and the other is similar to that is that okay to allow otherwise I see port 68 and 67 floods in my event log **(could this not changing IP be due to me blocking broadcast to external within firestarter?)**

edit to add - I don't have 192.168.100.1 and the other 192 address into my /etc/hosts file because the hosts file changes every time I boot Ubuntu so it just has the localhost and username-desktop entries is this okay or do I worry about spoofing attacks

---

