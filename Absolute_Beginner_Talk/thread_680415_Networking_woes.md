---
title: "Networking woes"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by davidwrocklage on 2008-01-27
Hello I have two Ubuntu computers that sit side by side, they are both connected to a D-Link 10/100 Fast Ethernet switch, both computers have access to the internet but so far I am unable to get the two computers to recognize each other for file sharing. Under "network" they both have "windows" networks. Originally this was a Ubuntu / windows xp network but I know am dual booting one computer and want my both my Ubuntu systems to file share.

---

### Post by emarkd on 2008-01-27
There are lots of ways to do this.  One common way is Samba.  See [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) for more information.

You could also use nfs or sshfs or several other things if the Samba info I gave above doesn't seem to do it for you.

---

### Post by flyingtiger on 2008-02-06
Question: What network device links the 2 PC's together? Both PC's share an Internet presence via the switch, but do they know each other exist? How will they find each other over the Internet?

Try using 2 NIC's in one ubuntu box with one NIC connected via the switch. Set this box up as a gateway. The other ubuntu box networks through the gateway to the switch to the Internet. Now the PC's can get to know each other.

---

### Post by njparton on 2008-02-06
You'll probably need to forward samba's ports to each of the computers in your router. Can't recall what they are off the top of my head.

I need to do this to access my samba shares when away from home via my netgear router.

---

### Post by hyper_ch on 2008-02-06
if both are Linux computers, you can remotely mount shares from the other computers with nfs:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

If one is Windows, go for samba...

Furthermore you could also use SSHFS (which I think is easier to setup than NSF, but on a local network it will decrease performance due to the encryption).

---

