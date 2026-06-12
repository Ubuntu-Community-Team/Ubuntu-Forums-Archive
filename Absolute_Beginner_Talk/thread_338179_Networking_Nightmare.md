---
title: "Networking Nightmare"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by vergeh on 2007-01-14
I've been having a great deal of problems trying to get my Airlink AWLH3026 Wireless PCI Adapter to work properly in Linux. It's one of the supported cards, and the description said it works fine out of the box.

However, I can't use the Network Manager. Add/remove programs will not let me install it. And when I tried "sudo apt-get install network-manager-gnome" as many websites suggested, I got:

Reading package list... done
Building dependency tree
Reading state information.. done
E: Couldn't find package network-manager-gnome

It seems my driver works properly. I even tried installing the stock windows drivers instead using ndiswrapper, and it gave me nothing. I'm all out of ideas, and I'm throwing in the towel. Can anyone help?

---

### Post by oyvindaa on 2007-01-14
Works just fine here mate, maybe you've to enable some repositories?

---

### Post by vergeh on 2007-01-14
Enable some whats in the where now?

---

### Post by gcordoba on 2007-01-14
Hi, 
I am not an expert but just an user.
I think that in your case it is an instalation problem. 
If the instalation source of Ubuntu is ok, the inatall process should provide the Network manager  by default .
Gustavo

---

### Post by Neobuntu on 2007-01-14
OK. Network Manager is when one plugs in a wired network cable, then your *ubuntu automatically uses that for the network. Thus when it is unplugged, wireless networking (pre-setup) is used. While that's cool, not everyone wants this. See the user guides; if you would like to set this up.

Perhaps you just want the network settings instead. This way you can enter you wireless network name (ESSID) to match your wireless router and be online. 

If you can not enter an ssid, your driver choice & device is not working. In this case, the simplest solution is to insert a wireless device that just auto magically works (a chip-set from a reputable company.) 

You indicate that you have checked up front and that is the absolute best way to do it. I think yours should just work (with matching wifi info on your net and enabled). 

Also, ndiswrapper is a Linux wireless module/driver that requires the actual Windows XP drivers (install ndis-gtk) and perhaps also blacklisting a native development driver that does not work well. This is only where one doesn't want to choose the simplest route and insert a (native supported) wireless device with well supported chip-set. ndiswrapper allows almost every crappy Windows wireless device to use it's XP (not 98 ) driver in *ubuntu. It's amazing but it's not the best. Native is better for your health (and sanity).

Of course, one does need to enable the sources of your choosing, to fully access the superior program management/downloading system. With a wired connection first, and stuck with a Windows only wifi card, just ```
sudo apt-get install ndis-gtk
```

---

### Post by seshomaru samma on 2007-01-14
> **vergeh said:**
> Enable some whats in the where now?




Read [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories") about enabling repositories

you will then be able to download network-manager-gnome

---

### Post by vergeh on 2007-01-14
I've tried enabling every repository. It still gives me that incorrect return on my terminal. Could it be a driver error that's causing Ubuntu to overlook Network Manager?

---

