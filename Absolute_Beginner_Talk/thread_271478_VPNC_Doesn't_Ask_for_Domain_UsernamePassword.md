---
title: "VPNC Doesn't Ask for Domain Username/Password"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2006-10-04
Im using network manager on edgy, ive imported my pcf file from my cisco vpn client on windows. I am asked for the vpn password which i inpput, but i should get a popup asking for a domain username/password, but i never do. Our company uses windows server 2000 and 2003 and active directory to authenticate users so the only way i can actually hit the internal network is to use vpn, any ideas how to fix this?

---

### Post by kjpus on 2006-10-05
My guess is that the information you say "missing" is in the vpnc configuration file. Check /etc/vpnc/YourProfile.conf file.

---

### Post by lo900 on 2006-10-30
thanks for the tip
vpnc is working fine for me. I've created /etc/vpnc/mycompany.conf and run it as:

pc# vpnc mycompany

it will ask for your password

Lo900

I have nm, wireless, wpa

---

