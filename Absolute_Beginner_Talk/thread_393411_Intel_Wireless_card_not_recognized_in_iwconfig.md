---
title: "Intel Wireless card not recognized in iwconfig"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by slkuhn on 2007-03-25
Hi all,
I am really trying to give Linux a shot but I am struggling getting the wifi on my laptop to work.

I am on a Dell XPS m1210
My wireless card is an Intel PRO/Wireless 3945ABG 
I have Ubuntu v 7.04.

In Feisty's 'Restricted Drivers Manager' it shows that the driver for my card is "enabled" and "in use". However if I got to System>Network, it does not display a wireless connection.

When I go into terminal and do 'iwconfig' gives:

lo        no wireless extensions.

eth0      no wireless extensions.

And that is all, When i do 'ndiswrapper -l" it gives:

installed drivers:
w29n51          driver installed (alternate driver: ipw2200)

No mention of my hardware being installed.

What Should I try doing now??

I really want to get this to work and if anyone can help me I will be very greatful.

---

### Post by Bachstelze on 2007-03-25
Did you install the restricted-modules matching your current running kernel ?

---

### Post by slkuhn on 2007-03-25
no I have not. Can you point me in the right direction. Im not sure what any of that means so I think I might need to be told.

---

### Post by Bachstelze on 2007-03-25
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

IF this machine is not connecte dot the Net, download the package from [http://packages.ubuntu.com](http://packages.ubuntu.com) on another machine, copy it with a USB drice or whatnot and install it manually with *dpkg -i*.

---

### Post by slkuhn on 2007-03-25
It gave me this information:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-restricted-modules-2.6.20-13-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.20-13-generic has no installation candidate


That doesn't look good. Do you know what this means? Thanks in advance.

---

### Post by crackling on 2007-03-25
Hmm, the way I got my wireless card working (the same as yours) was to install gnome-network-manager (not running on ubuntu currently so I don't remember if this is exact) via synaptic package manager and it started working fine. Also, you might want to consider using 6.06 instead since 7.04 is still in beta and probably won't be the easiest for new users to use.

---

### Post by Bachstelze on 2007-03-25
Nah, it will work fine in Feisty, just neets the restricted-modules installed.


EDIT : Hmm, actually, I noticed the drivers are available only for the 2.6.20-12 kernel in Feisty and you have 2.6.20-13 so you'll need to install the 2.6.20-12 kernel too.

---

### Post by Falados on 2007-03-25
> **slkuhn said:**
> Hi all,
I am really trying to give Linux a shot but I am struggling getting the wifi on my laptop to work.

I am on a Dell XPS m1210
My wireless card is an Intel PRO/Wireless 3945ABG 
I have Ubuntu v 7.04.

In Feisty's 'Restricted Drivers Manager' it shows that the driver for my card is "enabled" and "in use". However if I got to System>Network, it does not display a wireless connection.

When I go into terminal and do 'iwconfig' gives:

lo        no wireless extensions.

eth0      no wireless extensions.

And that is all, When i do 'ndiswrapper -l" it gives:

installed drivers:
w29n51          driver installed (alternate driver: ipw2200)

No mention of my hardware being installed.

What Should I try doing now??

I really want to get this to work and if anyone can help me I will be very greatful.

Did you try?:

'sudo ndiswrapper -m'

This command installs a line in modprobe.d so that it loads your driver at boot and aliases it as wlan0 or eth1 or something.

---

### Post by slkuhn on 2007-03-25
> **HymnToLife said:**
> Nah, it will work fine in Feisty, just neets the restricted-modules installed.


EDIT : Hmm, actually, I noticed the drivers are available only for the 2.6.20-12 kernel in Feisty and you have 2.6.20-13 so you'll need to install the 2.6.20-12 kernel too.


Im sorry Im so ignorant as to how to do much of this. But can you tell me how to install the 2.6.20-12 kernel too? You have been great for assisting me thank you.

---

### Post by slkuhn on 2007-03-25
> **Falados said:**
> Did you try?:

'sudo ndiswrapper -m'

This command installs a line in modprobe.d so that it loads your driver at boot and aliases it as wlan0 or eth1 or something.

I did that and it said:
modprobe config already contains alias directive

Thanks for your input though.

---

### Post by Bachstelze on 2007-03-25
[http://packages.ubuntu.com/feisty/base/linux-image-2.6.20-12-generic](http://packages.ubuntu.com/feisty/base/linux-image-2.6.20-12-generic)
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-12-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-12-generic)

Download, copy with USB disk, install with

```
sudo dpkg -i /path/to/file.deb
```

---

### Post by slkuhn on 2007-03-25
You are a Saint. I am on my wireless network now.
Thank you so much. Now I can focus my efforts on seeing what the big deal is with Linux... :)

---

### Post by macogw on 2007-03-25
> **Falados said:**
> Did you try?:

'sudo ndiswrapper -m'

This command installs a line in modprobe.d so that it loads your driver at boot and aliases it as wlan0 or eth1 or something.

Intel drivers don't use ndiswrapper.  They work by default generally, though apparently they went and put a kernel without restricted drivers in the repos again.

---

