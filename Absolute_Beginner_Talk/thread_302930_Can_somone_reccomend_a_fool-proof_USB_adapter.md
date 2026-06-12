---
title: "Can somone reccomend a fool-proof USB adapter?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by sheeep on 2006-11-19
I've given up on getting my microsoft adapter to work with ubuntu. So, could anyone recommend a wireless USB adapter that wont need an insane amount of tweaking for it to work?

---

### Post by David_T on 2006-11-19
Have you read this article?
[http://tips.linux.com/article.pl?sid=05/01/20/2251203&tid=100&tid=18&tid=121](http://tips.linux.com/article.pl?sid=05/01/20/2251203&tid=100&tid=18&tid=121)

---

### Post by jimmygoon on 2006-11-19
What are you talking about? Microsoft USB Adaptor what?

What is it adapting? I'm soooo lost.

---

### Post by sheeep on 2006-11-19
Woah, had a brain fart there. 

Can anyone recommend a wireless USB adapter for a wireless network that is known to work with ubuntu?

The one I have is refusing to.

---

### Post by eriefisher on 2006-11-19
I dual boot with XP and connect to my laptop with it wireless. I use a Netgear WG111NAR usb adapter. Although I have not tried to set it up with Kubuntu, it does show up with ifconfig and also shows up in the system settings/networksettings as active. That said, I don't think it would take to much to get it to connect to something.

eriefisher

---

### Post by sheeep on 2006-11-20
I'm a little nervous about any USB 2.0 adapters, previously when the laptop I have was running windows it had a lot of problems with a linksys adapter saying it was usb 2.0 and not compatable.

---

### Post by Azakus on 2006-11-20
Here's a list of usb 802.11g wifi adapters based on the Atmel chipset. The ones highlighted in green have a linux driver, so they're be easy to set up.

---

### Post by Crooksey on 2006-11-20
Got a link? :p

---

### Post by Azakus on 2006-11-21
I'm an idiot. There's a driver already in the supported repos for Prism chipsets. Just do 
```
sudo apt-get install linux-wlan-ng linux-wlan-ng-firmware
```
and use one of the cards listed [here]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")
Search through it for USB. I think I saw some 802.11g devices.

---

