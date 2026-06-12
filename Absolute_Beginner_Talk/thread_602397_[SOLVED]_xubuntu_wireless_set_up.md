---
title: "[SOLVED] xubuntu wireless set up"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tettayes on 2007-11-04
Hello, I have used ubuntu for a while now and I was thinking about using xubuntu since i heard it is faster.
now i face this problem of setting up wireless network on xubuntu.  I don't even see wireless connection icon on xubuntu desktop panel on the top which i usually see while using ubuntu.
therefore, i have no idea how to configure my wireless network.  I use intel wireless adapter which was already built in when i bought my laptop.

Could any one help with this issue??  any comments are more than welcome!

---

### Post by overdrank on 2007-11-04
> **tettayes said:**
> Hello, I have used ubuntu for a while now and I was thinking about using xubuntu since i heard it is faster.
now i face this problem of setting up wireless network on xubuntu.  I don't even see wireless connection icon on xubuntu desktop panel on the top which i usually see while using ubuntu.
therefore, i have no idea how to configure my wireless network.  I use intel wireless adapter which was already built in when i bought my laptop.

Could any one help with this issue??  any comments are more than welcome!

HI you can add it to the panel by right clicking. Then check under applications, system, network I believe and you will have to activate your wireless card. Hope this helps and good luck!

---

### Post by julian67 on 2007-11-04
If you're using Gutsy then it includes network-manager applet, the same as Ubuntu. If you're using Feisty or Edgy or Dapper then network-manager is not part of Xubuntu, so you have some choices.  You can use network-manager in Xubuntu and it works really well

```
sudo apt-get install network-manager-gnome
```

You would simply need to add nm-applet to your autostarted applications via the Settings menu.

An alternative is to download and install [wicd](http://wicd.sourceforge.net/)

> a wired and wireless network manager for Linux.

Wicd has many notable features, the most important of which are:

   1. No Gnome dependencies, so it is easy to use in XFCE, Fluxbox, Openbox, Enlightenment, etc.
   2. Ability to connect to wired and wireless networks
   3. Profiles for each wireless network and wired network
   4. Many encryption schemes, some of which include WEP/WPA/WPA2
   5. Remains compatible with wireless-tools 

Again you might want to add this to your autostarted list if you use a laptop and switch to new networks regularly.

Your Intel wireless card is fully supported by network-manager so either  nm-applet or wicd should work extremely well. If you don't mind some Gnome dependencies (which you are probably going to have sooner or later anyway) network-manager might be the better choice as dbus aware applications will know if you are connected or not. nm-applet also works very well with multiple network cards and I found it better than wicd for this. If you really are going to avoid Gnome libraries and want just a gui for network-config then wicd is a better choice.

---

### Post by tettayes on 2007-11-04
adding nm-applet in autostarted worked!
thanks a lot for the help!!!

---

