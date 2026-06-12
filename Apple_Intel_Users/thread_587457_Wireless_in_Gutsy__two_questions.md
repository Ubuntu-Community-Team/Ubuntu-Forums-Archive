---
title: "Wireless in Gutsy : two questions"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-22
In general the wireless connection to Ubuntu on my MacBook works flawlessly.
However, after the upgrade to Gutsy a few days ago, I notice that the wireless (in roaming mode) tends to select the SECOND strongest signal to connect to on boot rather than my own which is 3-4 times stronger.
I must then try to get the radio button in nm-applet for my network to accept my click which can take several attempts.
Is there anything I can do to get it to always select ONLY my network?

In an attempt to circumvent this annoyance, I took the Wireless Connection in Network Settings out of roaming mode and added in the ESSID and security key information.
This indeed worked very well in that there was no need to type in the keyring password and also no need to wait for the connection after the boot
However, it doesn't seem to be too reliable as occassionally, no connection at all is made and there doesn't seem to be too many options if this happens.
But why does it work sometimes and not others? Where I am, the wireless signal is very strong so I can't beileve that's a factor
Another disadvantage of this method is that the nm-applet no longer provides Connection Information (even though I specify DHCP which means the IP address is variable.

Grateful for any comments
Thanks
Paul

---

### Post by cyberdork33 on 2007-10-22
> **PaulFXH said:**
> In general the wireless connection to Ubuntu on my MacBook works flawlessly.
However, after the upgrade to Gutsy a few days ago, I notice that the wireless (in roaming mode) tends to select the SECOND strongest signal to connect to on boot rather than my own which is 3-4 times stronger.
I must then try to get the radio button in nm-applet for my network to accept my click which can take several attempts.
Is there anything I can do to get it to always select ONLY my network?

In an attempt to circumvent this annoyance, I took the Wireless Connection in Network Settings out of roaming mode and added in the ESSID and security key information.
This indeed worked very well in that there was no need to type in the keyring password and also no need to wait for the connection after the boot
However, it doesn't seem to be too reliable as occassionally, no connection at all is made and there doesn't seem to be too many options if this happens.
But why does it work sometimes and not others? Where I am, the wireless signal is very strong so I can't beileve that's a factor
Another disadvantage of this method is that the nm-applet no longer provides Connection Information (even though I specify DHCP which means the IP address is variable.

Grateful for any comments
Thanks
Paul
taking it out of roaming mode disables the use of networkmanger. That is a switch to use two different 'systems' of connecting. I can't really help you with the other issues, wifi is still in a young state on linux, there are occasionally such annoyances. You could try to file a bug (or search for a similar one).

---

