---
title: "Using Vista on 1 box and Fiesty on another - DNS issue"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Psquared on 2007-05-14
I have two boxes but one Motorala Cable Modem. The Vista box runs fine and the DNS addresses seem to be set correctly. However, when I disconnect the cables and put my Linux box up and connect everything I cannnot connect to the internet. I am NOT using a router.

My question is does Vista hijack the cable modem so that the Linux box cannot be reassigned the correct DNS through DHCP? In other words, the DNS addresses in /etc/resolv.conf are not the same as in ipconfig in Vista. 

Solution: Should I manually change the DNS addresses in Linux to those I see in ipconfig in Vista? Should I do this using NetworkManager or change the addresses in /etc/resolv.conf?

How about if I reconnect my router so that it will automatically reassign DNS addresses when I connect my Linux box. It would be no trouble to have two ethernet cables running from the router or I could buy a wireless node - either way.

Am I even close???

---

### Post by xpod on 2007-05-14
I`m no expert m8 but if you get your ip address via automatic dhcp and aint using a router then you should only need to reboot the modem if changing pc`s i think......i repeat "think":) 
i used to do the same myself till recently and a lot of times i would forget to reboot the modem when just changing the ethernet wire over hence the no internet?
I suppose you would have done that though eh??

I just use a second nic in to solve my problem as it`s only 2 pc`s on this connection but if you have a router then surely that is your best bet instead of howking wires in and out all the time

You should ask someone who knows for sure about these things though:)

---

### Post by BHelts on 2007-05-14
Yeah, you need to power cycle your Motorola modem in order to get internet access when crossing over PCs.  The reason is MAC address binding on your ISP's side, when you unplug from your Windows PC and Plug into Ubuntu, the modem will expect the MAC address of your Windows box, and it will not forward packets.  A $50 router will not only fix this problem but make you A LOT!!!!! more secure on the net.  Best of luck.

---

### Post by Psquared on 2007-05-14
> **BHelts said:**
> Yeah, you need to power cycle your Motorola modem in order to get internet access when crossing over PCs.  The reason is MAC address binding on your ISP's side, when you unplug from your Windows PC and Plug into Ubuntu, the modem will expect the MAC address of your Windows box, and it will not forward packets.  A $50 router will not only fix this problem but make you A LOT!!!!! more secure on the net.  Best of luck.


Hmmm... tried rebooting the modem with linux box attached but that didn't work. The DNS addresses in /etc/resolv.conf stayed the same. That's why I asked if I should manually change them. I should point out that I am using Fiesty, but not the final release version. I seem to remember some bugs in NetworkManager and DHCP with Fiesty Beta releases so I downloaded the final release version of Fiesty which I will install.

I like the idea of hooking up the router (hey I thought of that myself) which I already own. (A Linksys) The only reason I disconnected it was because I gave my laptop to my church and didn't need the wireless capability. It only occurred to me recently that this might be causing the problem with the DNS settings.

I also didn't realize that the computer controls the cable modem. So in fact Vista did hijack the modem - or the modem lacks the ability to reassign DNS addresses to a new computer. I guess that's why God made routers.

Thanks.

---

