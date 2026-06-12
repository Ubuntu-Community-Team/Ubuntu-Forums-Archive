---
title: "knetworkmanager problem"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-03-25
Hello, I have just installed ndiswrapper to get my netgear WG311 working, all is well.

I am connected to the network and there seems to be no problems other than knetworkmanager wont pick up that I am connected and appears although I am disconnected.

I am connected through device: ath0, how can I change knetworkmanager to monitor this device?

---

### Post by Kamu on 2007-03-25
The solution that owrked for me in a similar but not quite identical problem for me was the following:

cd /etc/network
sudo cp interfaces interfaces.backup

now choose you favorite editor:

emacs interfaces&

in the /etc/network/interfaces, comment out the lines relative to the interface you want the network manager to take in charge so for example:
auto ath0
iface ath0 inet dhcp

becomes
#auto ath0
#iface ath0 inet dhcp

If you find this doesn't help, just restore your backedup file
cd /etc/network
sudo cp interfaces.backup interfaces

---

