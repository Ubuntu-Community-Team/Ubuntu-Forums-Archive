---
title: "Broadcom............ help please!"
date: 2012-01-20
forum: Any Other OS
---

### Post by lwfitz on 2012-01-20
Hi I posted this over on the Mint forums and cant seem to get any help at all. 
Im running Mint 12 KDE but this issue has been on going for me on two different computers so Im really hoping someone can help.
I have a broadcom wireless card (bcm 4313) and have it working fine most of the time. I seem to have finally fixed the unstable/slow connection issue but I cant figure out why every time I reboot all of a sudden my wireless card doesnt see any networks. Then is I shutdown completely and boot back up it sees the networks fine. 
Any ideas? Im about to go crazy ](*,) #-o

---

### Post by Perfect Storm on 2012-01-20
Moved to Other OS/Distro Talk.

---

### Post by carl4926 on 2012-01-20
In kde now there is an option to make the wireless connection a system connection
Have you selected that?
[http://www.su2root.ukfsn.org/files/SUSE%20Misc/kde-wireless-new.png](http://www.su2root.ukfsn.org/files/SUSE%20Misc/kde-wireless-new.png)

Are you using b43 or did you install the offered proprietary driver?

---

### Post by lwfitz on 2012-01-20
> **carl4926 said:**
> In kde now there is an option to make the wireless connection a system connection
Have you selected that?
[http://www.su2root.ukfsn.org/files/SUSE%20Misc/kde-wireless-new.png](http://www.su2root.ukfsn.org/files/SUSE%20Misc/kde-wireless-new.png)

Are you using b43 or did you install the offered proprietary driver?


Yeah ive got that all set up and at the moment I have b43** installed. This is an issue Ive had with other distros also, including opensuse. 

Sorry bout posting in the wrong spot I realized it right after I posted. Thanks for moving.

---

### Post by lwfitz on 2012-01-21
This seems to not be a common issue so could it be that the wireless card is not functioning correctly?? Might be worth investing in a new one that isnt broadcom............ Maybe? Idk but Im sure frustrated with this!

---

### Post by kurt18947 on 2012-01-21
If you choose to get another WiFi adapter and are okay with Ebay,  I just bought a 'refurb' (it looked new) Dlink DWA-131 for $12.95 free shipping.  It uses a RealTek RTL-8192SU chip which has been plug & play for most people since 11.04/2.6.38 and should work with Mint 12.

---

### Post by carl4926 on 2012-01-21
> **kurt18947 said:**
> If you choose to get another WiFi adapter and are okay with Ebay,  I just bought a 'refurb' (it looked new) Dlink DWA-131 for $12.95 free shipping.  It uses a RealTek RTL-8192SU chip which has been plug & play for most people since 11.04/2.6.38 and should work with Mint 12.
Should be fine

---

### Post by lwfitz on 2012-01-21
> **kurt18947 said:**
> If you choose to get another WiFi adapter and are okay with Ebay,  I just bought a 'refurb' (it looked new) Dlink DWA-131 for $12.95 free shipping.  It uses a RealTek RTL-8192SU chip which has been plug & play for most people since 11.04/2.6.38 and should work with Mint 12.

Right on. Ill check that out. Thats an internal card right? This is going in a laptop so I dont want a usb card

---

### Post by lwfitz on 2012-01-21
> **carl4926 said:**
> Should be fine

These are the two I was considering.... any thoughts? 

1) [http://www.amazon.com/MN11BGN-Wireless-N-1T2R-PCIe-Mini/dp/B001FWEAL2?SubscriptionId=AKIAIM2F4YWBX2ZWXQMQ&tag=bewtest6-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B001FWEAL2]("http://www.amazon.com/MN11BGN-Wireless-N-1T2R-PCIe-Mini/dp/B001FWEAL2?SubscriptionId=AKIAIM2F4YWBX2ZWXQMQ&tag=bewtest6-20&linkCode=xm2&camp=2025&creative=165953&creativeASIN=B001FWEAL2")

2) [http://www.amazon.com/Ubiquiti-SR71-PC-Express-802-11a-400mW/dp/B004GIGOL6/ref=pd_sim_sbs_e_6]("http://www.amazon.com/Ubiquiti-SR71-PC-Express-802-11a-400mW/dp/B004GIGOL6/ref=pd_sim_sbs_e_6")

The Ubuquity card uses an Atheros chip which I believe is plug and play but Im not sure about the msi card. I sure dont want to buy one and have the same issue! lol! Thanks for the help guys.

---

### Post by carl4926 on 2012-01-21
Not sure how good my assessment or advice is
So: [http://linuxwireless.org/](http://linuxwireless.org/)

---

### Post by lwfitz on 2012-01-21
> **carl4926 said:**
> Not sure how good my assessment or advice is
So: [http://linuxwireless.org/](http://linuxwireless.org/)

That site was a huge help in a couple ways. First it told me basically that there is no support for my card, bcm 4313 seems to be one of the worst ones as far as support. 
Secondly it lit a fire under my *** and proved that I had lost my mind........ At 230am I pulled apart an HP dv6700 that is fried and put the wireless card from it into this Dell N7010. It took a little finessing since its not a mini card but I got it secured :guitar:

The new card is an ar5007 chip which I thought was plug and play but I guess I was wrong. Although it worked right away as soon as I rebooted it didnt recognize the wireless card. So I shut down completely and booted back up and there it was. Any ideas why it wouldnt recognize it on a reboot? Sort of similar to the broadcom  but a little different.

---

### Post by lwfitz on 2012-01-21
So I installed the windows driver and that fixed my issue when I reboot. The only issue left is for some reason my connection speed caps at 24mbps instead of 54mbps. Oh well Ill get that figured out. Thanks again for all the help!

---

