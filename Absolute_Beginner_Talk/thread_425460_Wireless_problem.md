---
title: "Wireless problem"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by programmer in linux on 2007-04-27
hello everyone

how i can install my wireless card

my laptop dell inspiron 640m
this Info. of my wireless card

Wireless Connectivity Solutions: Integrated Dual-Band (802.11 a/b/g & draft 11n) antenna. Integrated Intel®  Pro/Wireless 3945 (802.11a/b/g) or DellTM Wireless 1500 (Draft 802.11n and 802.11 a/b/g) network connections. The Dell Wireless 350 integrated Bluetooth 2.0 wireless solution is available at time of purchase only

---

### Post by agurk on 2007-04-27
Hi there. First, we need to know what wireless card you have. Now, you have listed both available options for your laptop:

* Intel® Pro/Wireless 3945 (802.11a/b/g)
* DellTM Wireless 1500 (Draft 802.11n and 802.11 a/b/g)

...but which one did you actually choose?

---

### Post by programmer in linux on 2007-04-27
* Intel® Pro/Wireless 3945 (802.11a/b/g)

thx

---

### Post by compmodder26 on 2007-04-27
Okay what version of Ubuntu are you using?  I've never had problems with the same card since 6.06.  Feisty (7.04) has been the easiest as it already has network manager installed by default, which I have always used to make wireless work.

---

### Post by programmer in linux on 2007-04-27
i have last version of Ubuntu 7.04

---

### Post by agurk on 2007-04-27
Ok, same as me then. :)

What you need to do is:

1. Connect your laptop to the Internet by using a wired connection
2. In System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Ubuntu Software tab, make sure you check the "Proprietary drivers for devices" checkbox.
3. Press the Reload button
4. Locate a package named "linux-restricted-modules-2.6.20-15-generic", mark it for installation and press the Apply button.
5. That's it (perhaps you need a reboot as well, I can't remember). Let us know if it worked.

---

### Post by compmodder26 on 2007-04-27
> **agurk said:**
> Ok, same as me then. :)

What you need to do is:

1. Connect your laptop to the Internet by using a wired conection
2. In System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Ubuntu Software tab, make sure you check the "Proprietary drivers for devices" checkbox.
3. Press the Reload button
4. Locate a package named "linux-restricted-modules-2.6.20-15-generic", mark it for installation and press the Apply button.
5. That's it (perhaps you need a reboot as well, I can't remember). Let us know if it worked.

* Note: These should have already been installed by default.  But it never hurts to look again.

Once you are sure that the restricted modules are installed, you can connect to your wireless network like this:

1.  You should see an icon in the upper right hand corner that looks like two computers overlapped.  They probably have an X through them.

2.  Left click this icon and you should see a list of wireless networks available near you.  Click the network you wish to connect to.

3.  If your network isn't listed, then click "Create New Wireless Network".  A new dialog box will pop up.  Fill in the required information.

4.  Your laptop should then attempt to connect to the network.

---

### Post by programmer in linux on 2007-04-27
okey i will try thx

---

### Post by programmer in linux on 2007-04-27
thx for u all 
it work

---

### Post by agurk on 2007-04-27
That's good to hear. :)

---

