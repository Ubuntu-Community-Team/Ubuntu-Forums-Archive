---
title: "NDIS Failure"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Tech_Analyst on 2007-03-08
ndiswrapper -i NetA3AB.inf
neta3ab is already installed. Use -e to remove it
ndiswrapper -l
Installed drivers:
neta3ab invalid driver!
ndiswrapper -e neta3ab.inf
Driver neta3ab.inf is not installed.Use -l to list installed drivers......

Reminds me of driver files in w98. 
I can not install or uninstall this driver. I have reinstalled ndis. Rebooted. Switched to root....
Help Please..

---

### Post by benfindlay on 2007-03-08
try typing ```
sudo apt-get install ndisgtk
```

This will install the graphical front-end for ndiswrapper into System>>Administration>>Windows Wireless Drivers

Allows you to configure everything with point and click!

Try removing everything through there!

Hope this helps!

---

### Post by Tech_Analyst on 2007-03-08
Hmm.. Don't I need internet connectivity to get ndisgtk

E: Couldn't find package ndisgtk

and thanks for the quick reply.

---

### Post by benfindlay on 2007-03-08
OOPS! Good point. I have the benefit of being wired as well! ](*,) 

You could always download it on another machine, copy it across via cd/floppy/memory stick and install it as follows:

((N.B. I am assuming the package is called ndisgtk.deb. If not replace the [ndisgtk] with whatever the package file is called!))

1. Copy [ndisgtk].deb file onto desktop
2. Launch a terminal window
3 Type the following:```
cd Desktop
sudo dpkg -i [ndisgtk].deb
```

Then you should be good to go!

EDIT: get your package from here: [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/]("http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/")

I recommend ndisgtk_0.6-0ubuntu1_all.deb

---

### Post by Tech_Analyst on 2007-03-08
ndisgtk installed. Driver loaded. Thank you. I am now off to find why my dwl-510 is still not working.

---

### Post by benfindlay on 2007-03-08
Its worth checking in your Network config that it is enabled, configured and active. I had problems for ages, until I suddenly realised that it was in fact disabled! ](*,) 

Also, are you totally sure you've got the right drivers. I personally have a netgear card, but it runs a realtek chipset, so I use the RTL8180 drivers instead of the official MA521 drivers!

Confusing or what!?

---

### Post by benfindlay on 2007-03-08
Just a checklist, that you did the following:

sudo ndiswrapper -i [your_driver].inf (used the GUI so should be fine!)
sudo ndiswrapper -l (to check the driver and hardware is ok)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

then this is important, because it makes your computer load ndiswrapper at boot:

```
sudo gedit /etc/modules
```
now add > ndiswrapper to the bottom of the file and save!

Now it might be worth getting a program called wifi-radar which is a wireless network detector, shows you signal strength, number of networks in vicinity, whether they are protected etc etc

Get that here: [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/w/wifi-radar/]("http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/w/wifi-radar/")

I recommend wifi-radar_1.9.7-0ubuntu2_all.deb

This will make it easier to tell if your card is picking up your wireless network.

Also found that I needed to reboot before everything worked for me!

Hope this helps!

---

### Post by Tech_Analyst on 2007-03-08
Thanks again for you help. I am comming up with a conflict in drivers. It seems in Network Tools I have wifi0 and ath0. In network settings it only shows ath0. I am showing traffic on the wifi0. Off to find out how to disable atho....:confused: ....

---

### Post by benfindlay on 2007-03-09
Not entirely sure but I believe theres a file called > /etc/network/interfaces

Might be worth you posting the output of ```
sudo gedit /etc/network/interfaces
``` here as it might provide an insight

---

### Post by sdotbailey on 2007-10-17
> **benfindlay said:**
> OOPS! Good point. I have the benefit of being wired as well! ](*,) 

You could always download it on another machine, copy it across via cd/floppy/memory stick and install it as follows:

((N.B. I am assuming the package is called ndisgtk.deb. If not replace the [ndisgtk] with whatever the package file is called!))

1. Copy [ndisgtk].deb file onto desktop
2. Launch a terminal window
3 Type the following:```
cd Desktop
sudo dpkg -i [ndisgtk].deb
```

Then you should be good to go!

EDIT: get your package from here: [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/]("http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/")

I recommend ndisgtk_0.6-0ubuntu1_all.deb


The mirror link you posted doesn't load up for me. Do you, or anyone, have any idea where I can get that ndis from?

---

