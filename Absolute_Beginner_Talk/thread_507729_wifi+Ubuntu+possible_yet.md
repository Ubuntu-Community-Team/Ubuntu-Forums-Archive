---
title: "wifi+Ubuntu+possible yet?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Zorrokan Zenovka on 2007-07-23
I just got Ubuntu going for the first time today from a live CD.  It's quite attractive.  Doesn't seem to notice my Netgear WG111v2 dongle which connects to a 2Wire Gateway: do I need to install to HDD connect wirelessly?

---

### Post by zipperback on 2007-07-23
> **Zorrokan Zenovka said:**
> I just got Ubuntu going for the first time today from a live CD.  It's quite attractive.  Doesn't seem to notice my Netgear WG111v2 dongle which connects to a 2Wire Gateway: do I need to install to HDD connect wirelessly?

There are a few different  methods for getting wifi up and running.

I don't have the same wifi card as you however as mine is an atheros chipset (works great with ndiswrapper).

search on the ubuntuforums.org website for:  Netgear WG111v2


It brings up several pages of information which should be able to get you up and running.


- zipperback :popcorn:

---

### Post by Fire-Eyes on 2007-07-23
if you figure it out let me know. I have been trying to figure that out for months now and nothing seems to work. Good luck. I am truly  cheering for you over here.

---

### Post by misfitpierce on 2007-07-23
It's possible just harder for some cards to confgure... Broadcoms are a piece of cake to setup now... just got to research your card.

---

### Post by AliL on 2007-07-23
If it is a USB dongle then it should work out-of-the-box according to this webpage: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

If it doesnt work on the live CD then it may be due to the fact that the live CD uses a stripped down version of the linux kernel so not all features are available. This is because to run a full Ubunutu distro on a live CD you'd need it on a DVD because Ubuntu is about 3GB when installed and you'd need a hell of a lot of RAM and to keep accessing the DVD drive.

Try installing Ubuntu on the machine and the dongle should just work.

However if you are using the WEP encryption protocol to protect your network then you may be unstuck as the webpage i gave above says (No WEP) in the comments. In that case you may have to remove the encryption or invest in a more linux friendly wireless dongle. But don't take my advice as the gospel truth for I am just a lowly linux newbie and there may indeed be a way around your predicament however I do not have the knowledge to help you any further I'm afraid.

Hope this was at least some help.

AliL

---

### Post by Zorrokan Zenovka on 2007-07-25
thanks all

I installed Ubuntu to my HDD and I hope to see some progress soon on the wifi front.  

ttyl


ZZ

---

