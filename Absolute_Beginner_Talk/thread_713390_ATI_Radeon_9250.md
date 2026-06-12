---
title: "ATI Radeon 9250"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by christophicer on 2008-03-02
Trying to get my ATI radeon 9250 256 mb graphic card to work.
I have on board and when i disable it i cant get anywhere because the ubuntu load screen freezes. I have tried just about everything and i just dont know what else to do. Does anyone know of anyway to get my graphic card to read without disabling the onboard. because as soon as i disable the onboard all the problems start. please
someone has to have something

---

### Post by djbsteart1 on 2008-03-03
What have you done so far? have you done the howto for ati cards under multimedia? or envy?

---

### Post by christophicer on 2008-03-03
done them both. envy sucks by the way... doesnt work with any ubuntu i have tried but tried the open source driver, tried the closed, tried the ubuntu how to. tried everything i know and can find.

---

### Post by djbsteart1 on 2008-03-04
It worked for me, but the driver didnt. I'm soory to say that I cant be much more help than this. Have you tried editing the xorg.conf file? Reconfigure the xserver?

---

### Post by uberlube on 2008-03-04
You also have to realize that ATI is just now starting to open up their drivers to the open source community and its going to tale some time for us to integrate them into Linux. You cant expect it to work out of the box or even with envy. You should grab yourself an nvidia.

---

### Post by BillDozer on 2008-03-04
> **christophicer said:**
> Trying to get my ATI radeon 9250 256 mb graphic card to work.
I have on board and when i disable it i cant get anywhere because the ubuntu load screen freezes. I have tried just about everything and i just dont know what else to do. Does anyone know of anyway to get my graphic card to read without disabling the onboard. because as soon as i disable the onboard all the problems start. please
someone has to have something

I had the same problem. It looks like Ubuntu freezes, but it doesn't. What happens is that although you have set the onboard card to be disabled in BIOS, Ubuntu (Linux in general) still sees the onboard graphics card.

Here is what I did:
[LIST]
[*]Disabled the onboard card.
[*]Started Ubuntu, still with the monitor in the onboard card
[*]After log in, System / Administration / Screens and Graphics
[*]Disable the onboard card
[*]Restart machine and plug cord into PCI graphics card.
[/LIST]

---

