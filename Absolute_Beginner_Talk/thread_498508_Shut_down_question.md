---
title: "Shut down question"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-07-11
Not a critical question.

In Windows, when I shut down the computer the nic is powered down. Both the nic's led and the routers connection lights go out. In Linux (Edgy, Feisty, and UStudio) both the nic's and the router's lights stay on. 

My suspicion is a "wake on lan" setting in Ubuntu. However, I never set that up. 

Any thoughts?

Edit-- I should mention this is a desktop system.

---

### Post by alienexplorers on 2007-07-11
In my system when I power off everything is powered off.  The only time the nic and router lights stay on is if I hibernate the computer.

---

### Post by lynxus on 2007-07-11
I cant see how ubuntu would effect this? Have you checked the bios for wake on lan being enabled?

---

### Post by Patrick K on 2007-07-12
I really don't see how this happens, either. I haven't checked the BIOS but will on the next boot.

---

### Post by 3rdalbum on 2007-07-12
I have heard of this before; there are people who have already posted complaining about this. Unfortunately, to my knowledge, they didn't find a solution. Is it important?

---

### Post by Patrick K on 2007-07-12
I rebooted and entered the BIOS, to my surprise, WOL was enabled. I disabled it but the nic still stays on when I shut down. 

It isn't important I guess, just a minor annoyance. I've been using the switch on the power supply to cut the juice use. I'm trying to reduce my household power use to the absolute minimum.

---

### Post by smellysocks on 2007-07-12
Both my machines at home are dual boot ubuntu and XP and both have an active network card when the machine shuts down from an OS. In theory it should have nothing to do with the OS but in your case it would suggest something is making the network card power down as such. When the card is inactive after shutting windows down what happens if you switch the machine off at the back or plug socket and then switch it back on without booting hte machine up?

As a side note I look after 800+ windows XP PCs with a couple of other people for my day job. On all our PCs the network card stays on when the machine shuts down and is generally what I presumed happened on all machines. The machines we have range from core 2 duos down to p3 based celerons for the older models. Around half of our machines have previously run windows 2000 and the NICs stayed on after shutdown using that OS too. We always have WOL set as we use it to remotely boot. I've just turned WOL off on one of them and the NIC still stays active after shutting windows down.

---

### Post by Patrick K on 2007-07-12
Interesting post, thanks. 

I have two machines, one W98 only. Both shut down their cards on system shutdown. Maybe this is a W98 thing and later versions are different. I assumed if WOL was disabled, there would be no reason for the nic to remain active. I agree the OS shouldn't make any difference (another thing that shouldn't be effected by the OS is the noise the sound card makes at shut down. Linux makes a very loud racket but W98 makes almost no sound). 

Switching off the rear power switch, after normal shut down in Linux, shuts down the NIC. Turning it back on leaves the NIC powered down. 

This system is a older MSI mobo with an integrated Intel NIC. CPU is P4 1600. I've never had any problems and it has the latest BIOS updates.

---

### Post by smellysocks on 2007-07-12
When you turn the power off at the back of the power supply the NIC will switch off as there is no power getting to the motherboard to provide power to the NIC. It's interesting that it the NIC stays off when you switch power back to the machine. Unfortunately you've gone beyond the realms of my hardware knowlegde. To confuse things more I've found that if I unplug the network cable from my test machine at the wall but leave it in the NIC (MSI board P4 1.7) and shut windows down the NIC shuts down. If I leave the cable in at the wall the NIC stays on when I shut wndows down. This is with wake on lan switched off. On all of our hardware if a machine is switched off at the wall or power supply the wake on lan funtion no longer works until windows has been started up and then shut down again. I'm not sure if this is due to some instruction given to the card by the OS on shutdown which is then lost when the card/motherboard loses power or purely a hardware characteristic of the NIC. We use different NICs so it is most likely the former. Again, I think I'm adding unneccessary confusion to the issue. I'll leave this to someone with more knowledge than me. I hope you find out what it is because it's got me curious too.

---

