---
title: "Installing wireless on Ubuntu"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by rjst on 2008-03-14
I am from a long Microsoft background and this is my first try at Linux, so forgive me if this seems rather school boy.

I want to install/activate my wireless adapter on my HP nx9420. I have install Ubuntu 6.06 server edition without LAMP (I am planning installing this later by hand for the learning curve). From searching around I believe I need to install “ipw3945” drivers. Much of the articles on the web say to download and install however during installing Ubuntu it seemed as though all necessary drivers were being installed.

So what I did was run from the shell “find –name ipw3945*”

./lib/modules/2.6.15-51-server/kernel/drivers/net/wireless/ipw3945
./lib/modules/2.6.15-51-server/kernel/drivers/net/wireless/ipw3945/ipw3945.ko
./lib/firmware/2.6.15-51-server/ipw3945.ucode
./proc/irq/185/ipw3945
./sys/module/ipw3945
./sys/bus/pci/drivers/ipw3945

Does this mean this driver is already installed I just need to activate in someway.

When I run iwconfig (iwconfig & ifconfig seem to be the same as ipconfig in windows) it just says.

Lo      no wireless extensions

Eth0  no wireless extensions

Can anyone help please?

---

### Post by Chris Kupka on 2008-03-14
You'll probably have to use ndiswrapper.  Run a search for "ndiswrapper" and your specific driver in the forums.  Odds are somebody's had your problem before, and there's a preexisting thread or tutorial that could help you out.

Ndiswrapper didn't work for my driver - I had to use a program called madwifi.  Still most people here seem to use the former program, so I'd start with that...

---

### Post by handydan918 on 2008-03-14
Try ```
sudo modprobe ipw3945
```

Then try iwconfig again.

It may be easier to do a reboot after the modprobe if the iwconfig doesn't work...

---

### Post by rjst on 2008-03-16
When I run this command "modprobe" I have no errors returned but iwconfig seems to show the same message as before, even after a reboot. Any ideas?

> **handydan918 said:**
> Try ```
sudo modprobe ipw3945
```

Then try iwconfig again.

It may be easier to do a reboot after the modprobe if the iwconfig doesn't work...

---

### Post by cjsteele on 2008-07-10
see [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420) for information.  There's a snipet at the bottom about wifi sucking as shipped in 8.04...

---

### Post by reilus on 2008-07-11
I cheated and ran Ubuntu Ultimate Edition.  It has the wireless all set up for you.  You can go about hardening the system later, but most of the stuff you need is already there.   

Maybe it will work out for you.  :guitar:

---

