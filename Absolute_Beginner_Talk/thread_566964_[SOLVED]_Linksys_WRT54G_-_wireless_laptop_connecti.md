---
title: "[SOLVED] Linksys WRT54G - wireless laptop connection"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by overandunder on 2007-10-04
Sorry if this has been covered before, but here goes.

I have a PC (running Feisty Fawn) with a broadband connection and the Linksys WRT54G router (connected via ethernet cable) which connects and runs perfectly.

Yesterday I installed Feisty Fawn Ubuntu from CD onto my laptop (which has a built-in 802.11g wireless card), but cannot get it to connect.

The same hardware setup ran without a glitch when both machines were running under XP. I ran iwconfig on the laptop - and it produced device (ra0) no problem.  Next I tried;

iwlist ra0 scan

this listed not only my own WEP encryped network but also both my neigbours' private networks! So I guess the hardware is ok - can anyone give me any pointers please or other things to check? Thanks

---

### Post by Lambert on 2007-10-04
> **overandunder said:**
> Sorry if this has been covered before, but here goes.

I have a PC (running Feisty Fawn) with a broadband connection and the Linksys WRT54G router (connected via ethernet cable) which connects and runs perfectly.

Yesterday I installed Feisty Fawn Ubuntu from CD onto my laptop (which has a built-in 802.11g wireless card), but cannot get it to connect.

The same hardware setup ran without a glitch when both machines were running under XP. I ran iwconfig on the laptop - and it produced device (ra0) no problem.  Next I tried;

iwlist ra0 scan

this listed not only my own WEP encryped network but also both my neigbours' private networks! So I guess the hardware is ok - can anyone give me any pointers please or other things to check? Thanks


The device and driver are working fine. How are you trying to configure and connect? If you're using the normal network management tool (icon on top panel or app under administration called network) It won't work with the device/driver you have.

I'm not up to speed 100% on this but believe you need to look into an app called RutilT for a graphical program to use.

You can post over in the network & wirelss section for a little more help.

I see you're also using the command line and that can be used to connect. You can read more on the command iwconfig by typing

```

man iwconfig

```

When Gutsy is released shortly, there is an updated version of network manager being released with it. 0.6.5 and I believe your card will work with that version as they've improved support for this chipset. (It still won't do wpa though if you're thinking of changing encryption method)

---

### Post by overandunder on 2007-10-05
Thanks for the reply.

As this was a new install and after looking around I downloaded the beta version of Kubuntu 7.10 (Gutsy Gibbon) to CD and did a fresh install and everything ran perfectly!

Although I am keeping my fingers crossed as its a beta release, the other problem I hadn't managed to tackle, namely poor 'fuzzy' graphics (which I suspected to be a driver issue) was also 'cured'.  By the way if it proves useful my Wifi card has an RT2500 chipset running WPA encryption (which others here have had trouble with over wireless) and my laptop is based around the SIS chipset.  Very impressed so far!

Thanks again.

---

