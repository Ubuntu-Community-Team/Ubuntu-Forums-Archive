---
title: "VPN hell .."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-23
How does one set up VPN on Feisty to access a remote server - i.e. a Windows Server?
I have looked at numerous websites but none seem to work.
When I right click on the Network Manager applet at the top of the screen, it only shows the checkbox "Enable Networking".

Any help would be appreciated.

Carl

---

### Post by dstew on 2007-05-24
Have you installed a VPN client? Your remote network administrator may be able to provide one best suited to the network they have. Otherwise, you can try OpenVPN. Get it using the Synaptic Package Manager.

But that is Edgy, maybe Feisty already has a VPN client installed, I don't know.

---

### Post by compiledkernel on 2007-05-24
the VPN client bits are in Add/Remove CW.

---

### Post by reckless2k2 on 2007-05-24
VPNC is pretty easy to use as long as you know all of your connecting info. You can use the default config or create your own config files with all the connecting info. 

My job had to put me in a defining connect group such as "users" or "remoteprog" in order to connect using the Cisco client.

---

### Post by lamalex on 2007-05-24
it depends what kind of vpn you're trying to connect to, is it a cisco vpn? openvpn? and MS vpn? all vpns are not equal, find out from your sysadmin what kind of vpn is it.

---

