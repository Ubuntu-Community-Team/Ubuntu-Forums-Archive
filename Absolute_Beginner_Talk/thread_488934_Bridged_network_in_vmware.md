---
title: "Bridged network in vmware"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Herix on 2007-06-30
I set up my vmware and Im trying to make it use my secondary NIC instead of having it use the same adapter as my laptop. However, whenever I select **bridged** in the configuration tab I cant connect to the internet nor ping my router. What is strange is that it gets a DHCP assigned by the router which tells me that there is a connection whatsoever. When I configure my VM to share the same IP as my laptop (NAT) everything works fine.

I have an wired ethernet connection and a wireless card both connected to my router. How can I make my laptop use one card and my VM use the other card?

Thanks.

---

### Post by Computer-Geek on 2007-07-01
Can u give me the setup of ur networking?
Thanks!!

---

### Post by Herix on 2007-07-01
> **Computer-Geek said:**
> Can u give me the setup of ur networking?
Thanks!!

Im sorry I dont understan what you mean by the setup of my networking. but I can tell you that I have two computers connected to my router: one laptop and one desktop. In my laptop I have two  network cards: one wired and one wireless. Both cards are connected to my router, and I want to use one of my two cards dedicated to my VM.

I hope this is what you need to know.

thanks.

---

### Post by -Vampyre- on 2007-07-02
I have vmware setup on my laptop. Internet works fine on virtual pc through wired connection. I haven't figured out how to switch it to the wireless.

---

### Post by Herix on 2007-07-05
Long time after....., I figured it out. But I post it here so that others can see:

While i was reading thru  logs in /var/log/messages, I read I line that warned me that wireless bridge is not supported if you use any-any-update in vmware. 

For those who dont know, any-any-update is a patch that fixes  a problem when installing VMware Server.

I hope this helps somebody.

---

