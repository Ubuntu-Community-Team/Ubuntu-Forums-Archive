---
title: "Linksys Wireless N USB Driver help"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by crackerXcore on 2007-06-07
Model name: WUSB300N

Its a wireless usb network adapter. I need it to work. Linksys doesn"t have the drivers and I have no clue how to install my own.

I just made a dual boot with XP and I want to transition to Linux but its hard without internet!

I just graduated High School with hopes of a computer engineering degree and I can't wait to finally see why linux is great. I would appreciate any help!

EDIT: I do have the .inf and .sys files, when i did a google search someone mentioned using the windows drivers in a wrapper. I have no clue what this is.

---

### Post by Najand on 2007-06-07
1) Plug in to LAN and get internet
2) Install network-manager
3) type this command into the terminal:
```
sudo gedit /etc/network/interfaces[/CODE}
and add:
[CODE]
auto eth1
iface eth1 inet dhcp

```
Restart your computer and try again.

---

### Post by jiminycricket on 2007-06-07
Hi,
another thing you can do is install ndiswrapper or ndisgtk (for a graphical utility) to wrap the Windows drivers that you have.

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

This person has indicated that he got a Linksys N card working in Linux: [http://www.gossamer-threads.com/lists/mythtv/users/260902](http://www.gossamer-threads.com/lists/mythtv/users/260902)

---

### Post by VictorCain on 2007-06-13
If I can figure out how to import a file, this shows how I got the WUSB300N working in Kubuntu (7.04):

---

