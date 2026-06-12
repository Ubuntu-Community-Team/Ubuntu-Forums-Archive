---
title: "Internet Connection"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-19
Is it possible to configure my internet connection so that it doesn't try to connect until the first time I start FireFox? The reason being that my firewall (Firestarter) seems to be a bit slow in getting itself "ready" and I'm never quite sure whether it's actually operating or not. I've selected an option in Firestarter to display an icon on my menu bar but it never seems to display the icon unless I start the firewall manually.

---

### Post by ozorba on 2006-12-19
First, are you using an ethernet/wireless connection? If that is the case you can permanently disable it. 

Generally the network connection code is executed when you start up the pc.

---

### Post by pandu.rs on 2006-12-19
This tell how to make ur firestarter load at startup

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

BTW, even if firestarter is not shown the systray, ur firewall is started at system startup!

---

### Post by John E on 2006-12-19
Thanks pandu.rs - I've already got it set up to be started at system startup but something (either Firestarter or my ADSL modem) doesn't settle down until about 20 seconds after booting up. Therefore I need the following:- (a) to delay my internet connection so that it doesn't connect until I first launch Firefox - and (b) to delay Firestarter so that it doesn't run until I first connect to the internet.

ozorba - it's a USB broadband modem. I don't mind my local network connection starting at startup - but I don't want to be connected to the internet until everything's settled down.

---

### Post by John E on 2006-12-19
I guess this isn't possible then...?

---

### Post by mr_samsonov on 2006-12-19
I think firestarter will already be started before your firefox opens up. Just because the icon has not appeared I think you will find firestarter is still running already. 

After all firestarter just configures your iptables, which will not have changed since your last boot if my understanding is correct.

---

### Post by John E on 2006-12-19
No, I've already established that it fails to start. In fact, if I try to start it manually within that initial 20 seconds after boot-up, it consistently fails to start.

Here's something weird though.... I've only just realised that I don't actually know _how_ I'm connecting to the internet anyway. At no time have I been asked to enter the user name or password that I use for logging in via my ISP. And yet I can connect to the internet and surf the web as though I was logged in. :confused:

---

### Post by jvc26 on 2006-12-19
Isnt firestarter just a GUI for editing the iptables? iptables runs all the time I thought. The USB modem - does that have the information stored in it like a router? As my router just was set up once and then acts as the gateway which is automatically used.
Il

---

### Post by John E on 2006-12-19
> **Illuvator said:**
> Isnt firestarter just a GUI for editing the iptables?

I don't think so - it offers many of the features that are found on comprehensive firewalls such as port forwarding, internet connection sharing and DCHP server.

> **Illuvator said:**
> The USB modem - does that have the information stored in it like a router?

I suppose it's possible but I'm pretty certain it doesn't.

---

