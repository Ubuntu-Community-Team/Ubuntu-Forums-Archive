---
title: "Very Slow Network / Internet Speed using BCM4306 chip (default card) in G4 Powerbook"
date: 2012-09-12
forum: Apple Hardware Users
---

### Post by standarshy on 2012-09-12
I'm using a G4 Powerbook running Ubuntu 12.04.

My problem is that my internet is really slow using the default card.  The chip is a BCM4306.  Currently, the b43legacy drivers are installed.

When I use other usb wireless cards (which use different drivers such as RA), they work much better.

I'd really appreciate it if someone could help me get this computer's card running at regular wireless G speeds.

Thanks

---

### Post by 2blue on 2012-09-12
I bumped into [this]("http://askubuntu.com/questions/99405/bcm4306-slow-speeds-when-set-to-54mbps") the other day, others seem to have similar issues with the BMC4306 card. Hope you can make some thing of it.

---

### Post by standarshy on 2012-09-12
Thanks again 2blue. I've taken another look but I'm not sure if that'll help me since I think my card is a rev.1. I think he should have actually used the new drivers since his is rev.2 .  I've somewhat given up; I bought another wireless card the other day and all works well. It is using the RALINK drivers.

However, I'm still interested in other suggestions since it would be nice to just use the internal card.

---

### Post by 2blue on 2012-09-12
Yeah, use the usb one for now, and keep you eye up for solutions. You are probably not the only one with the card on debian related linux. I wonder what the options are outside the b43 stuff?

---

### Post by standarshy on 2012-09-13
2blue,

There are the Ralink and Atheros chips that use rt drivers and ath drivers respectively.

---

