---
title: "setting up internet connection at the university"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by kellogs908 on 2008-01-13
Here is a how to for setting up the internet conenct at niu, my university but its for suse and I cant get it to work quite right with ubuntu, is there any reason it wouldnt work with ubuntu, if it should work is there anyways someone can post a quick how to, or adjusments that need to be made becuase its ubuntu

thanks

---

### Post by moffa on 2008-01-13
Please provide details of what you need to setup.  Is it wireless or wired?  Network manager should do sufficient unless you're using a VPN connection.

---

### Post by kellogs908 on 2008-01-14
its wireless 
here is teh how to for SUSE
[http://securenet.niu.edu/wpasuse10x.shtml]("http://securenet.niu.edu/wpasuse10x.shtml")
they use a vpn client for windows, you have to install a program to make it work, but it says on the tutorial you dont ahve to install anythign for linux

---

### Post by moffa on 2008-01-14
You can try openvpn, I personally did not have much luck with it.

---

### Post by kellogs908 on 2008-01-14
no luck thus far, anything else I can try

---

### Post by jordanmthomas on 2008-01-14
Networkmanager should work fine.
Have you got wpa_supplicant installed (it's in universe)?

If so, and your wireless card is working, you should be able to connect after providing the key.

also, it is possible to enter this all on the command line if networkmanager is being flaky.

You'll probably find these commands helpful (don't know the exact syntax you need to give iwconfig offhand but look it up, it's simple):
iwconfig
and ifconfig

---

### Post by kellogs908 on 2008-01-15
hey guys I don't know how to change my network card preferences if could tell me how I would appreciate it

---

