---
title: "Router/modem problems"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by sarum on 2008-01-25
Hi, I asked this question a few days ago; two replies and I thought I might have had the answer, but after much fiddling, I'm back where I started but this time with an other modem. I signed up for broad band and got it working very well on an XP machine.
 The modem/ router is a D-Link ADSL2+ Router and is connected to XP via USB.
 Ubuntu is connected via Ethernet cable and the light on the modem lights up. I think, (being a newby) that I need to config: a bit more on the Ubuntu. When I go to admin:/network settings there's a blue 'phone icon(not ticked) from dial-up days; and 'Wired Connection' which I have ticked and set at DHCP. The wire from modem to Ubuntu came with the modem.
If I need to go to 'admin/network tools' I shall have to have very clear instructions. But I'm not afraid of the CLI stuff. Thanks to you all for so much help in the past.............sarum

---

### Post by FreewheelinFrank on 2008-01-26
What happens if you try to access your router by typing this address in the address bar of Firefox?

> [http://192.168.0.1](http://192.168.0.1)

---

### Post by sarum on 2008-01-26
FreeWheelinFrank. I have no idea how many hours I've spent trying to get this thing to work. I've 3 Ubuntu books and FAQ's - and one easy suggestion from you and it works.
Thankyou SO MUCH..............sarum

---

### Post by FreewheelinFrank on 2008-01-27
If it works, it just means there is no problem with the connection between your computer and your router.

To get a connection from your computer to the internet, check the settings on your router.

Under LAN Settings, I have:

>  DHCP Server	Enabled

And in Ubuntu, Network Settings>Connections>Wired connection>Properties>Configuration is set to Automatic configuration (DHCP). (The default was Enable roaming mode, and that worked too.)

In the DNS tab of Network Settings, the address and name of my router show up.

Can you connect to the internet?

If not, what error message do you get?

Check your router and Ubuntu Network Settings. If your router is not set to use DHCP, you may have trouble connecting.

---

