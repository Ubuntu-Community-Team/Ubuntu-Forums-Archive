---
title: "Wireless problem continued"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by PlasticWorm on 2007-04-22
Sorry for a new thread, but I've got another problem that seems to be more specific. I've installed ndiswrapper and installed the driver for my WUSBF54G USB network adapter. The driver is recognized and so is the hardware.

I was directed to get wlassistant, which I installed. Then "gksudo wlassistant".

It started and stated no wireless devices found.

iwconfig shows that there is nothing.

Under System > Admin > Networking, the only options are Wired and Modem.

---

### Post by mabelrxu on 2007-04-22
what does your /etc/network/interfaces file say?

it should have at least
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```
and maybe one other one if you're ever planning to actually use your modem, but i don't know what that one should be ( ... possible candidates include auth0, wlan0, and eth2, and maybe others ... )

---

### Post by tirofiban on 2007-04-22
Hi,

This probably isn't what you want to hear but....

I've been using Ubuntu on several different computers for almost 2 years now. 

I think I tried using NDIS wrapper on the same usb adapter you have when I was a beginner. I could never get it to work. For about a year now, I used NDISWrapper on a Broadcom chip and it was always awkward, (ie sometimes the only way to turn the card on was to boot into Windows and then boot back into Ubuntu and then the wireless light would come on.)

When I think about how much time I've wasted trying to get NDISWrapper working, I realize I could have been doing better things with Ubuntu. 

In my opinion, it's best to use a wireless device that Ubuntu has a driver for. I just took apart my laptop this weekend to replace the awful broadcom card with an Intel card. The new card worked right out of the box, WPA and everything. I was kicking myself for not doing it sooner.

From now on, I'll never use NDISWrapper, and with the time I'll save, I'll be doing my homework on what works out of the box with Ubuntu. 

Also, don't forget other options, like Airport express and Wireless Bridges, where Ubuntu doesn't even need to know that it's using wireless.

This is just my opinion. For all those people using NDISWrapper flawlessly, well you're a lot smarter and more talented than me.

Good luck!

---

### Post by PlasticWorm on 2007-04-22
> **mabelrxu said:**
> what does your /etc/network/interfaces file say?

it should have at least
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```
and maybe one other one if you're ever planning to actually use your modem, but i don't know what that one should be ( ... possible candidates include auth0, wlan0, and eth2, and maybe others ... )

Same, it goes up to eth4 and has a wlan0 with pretty much the same line, I believe. 


Thanks tirofiban, I'll keep trying until I get the cash to throw down for a new device. Any recommendations for one? USB or PCI, which one is better in this case?

---

