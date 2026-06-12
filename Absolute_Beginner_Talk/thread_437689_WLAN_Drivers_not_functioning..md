---
title: "WLAN Drivers not functioning."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by adam93250 on 2007-05-09
I have used Ndiswrapper to install the drivers.

When i type ```
ndiswrapper -l
``` it comes up with ```
bcmwl5 : driver installed
```
I tried the other driver file, and its invalid.

Can anyone help?

---

### Post by Bachstelze on 2007-05-09
Wrong drivers. What kind of wireless adapter do you have (PCI or USB) ?

---

### Post by adam93250 on 2007-05-09
Its the Built-in WLAN for Comaq Presario V4000 (V4215EA)

System Spec.
Intel Celeron M Processor
1GB Ram
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

Anything else, just ask.

---

### Post by adam93250 on 2007-05-10
Ok, i have put the system specs in the post above.
If anybody could help i would be grateful.

'A laptop is not a laptop if it cannot go wireless'

---

### Post by adam93250 on 2007-05-11
Just great.
I had the wireless working last night, but now it doesnt even notice the wireless chip is there.

---

### Post by nickthegreek78 on 2007-05-11
go into system/ admin/ network / reconfigure wireless connection and if you are using broadband make sure DHCP is enabled

---

### Post by adam93250 on 2007-05-11
Thanks for trying to help, but thats where it has gone missing.

When i goto System -> Administration -> Network. I have the Network Settings Dialog, but there is no wireless option there.

---

### Post by nickthegreek78 on 2007-05-11
another option would be to re install the drivers from the manufacterrs site

---

### Post by nickthegreek78 on 2007-05-11
something else I thought of, you could try to update the ubuntu device database in system /preferences/hardware info/ at he bottom is  link to update

---

### Post by adam93250 on 2007-05-11
i suppose i could do that, as i do have the drivers still on my comp.
BUT, when it wasnt working last time (without drivers) i could still see the device in the Network Settings.

---

### Post by adam93250 on 2007-05-11
and, as soon as i try to use the Ubuntu device database collection Network Test, it freezes the test.

---

### Post by nickthegreek78 on 2007-05-11
go into network tools and click ping button, type in your ip address and ping if it is able to send and receive packets you should be able to go back into network and reconfigure the adapter i had this problem a few days ago wireless worked intially and then next re boot nothing.  ping solved the issue

---

### Post by adam93250 on 2007-05-11
nothing happens.

Just checked, driver is still installed.

---

### Post by adam93250 on 2007-05-11
ok, seeing if a restart will solve anything.

---

### Post by adam93250 on 2007-05-11
Ok, restart hasnt done anything. wireless still doesnt show up as a device.
Under Network Settings -> Cconnections, all i have is Wired Connection.

---

### Post by apienk01 on 2007-05-11
Try this:

1. Uninstall ndiswrapper:

```
sudo apt-get remove ndiswrapper
```

2. Edit blacklist:

```
 sudo gedit /etc/modprobe.d/blacklist
```

3. Type the following at the end of the file, then save and exit:

```
blacklist bcm43xx
```

4. Remove driver module:

```
sudo rmmod bcm43xx
```

5. Reinstall ndiswrapper:

```
sudo apt-get install ndiswrapper
```

6. Download driver from [here]("http://www.box.net/index.php?rm=box_v2_download_shared_file&file_id=f_20739252").

7. Unpack the archive:

```
tar zxvf wifi-drivers-x32.tar.gz
```

8. Install and check the driver:

```
sudo ndiswrapper -i bcmwl5.inf
 sudo ndiswrapper -l

```

9. Edit */etc/modules* and add * ndiswrapper* at the end.

10. Reboot or type:

```
sudo modprobe ndiswrapper
sudo /etc/modprobe.d/networking restart

```

---

### Post by adam93250 on 2007-05-11
Thanks for the reply but no.
The device still does not appear.

Like i said, last time the wireless did not work, the device still showed up.

---

### Post by adam93250 on 2007-05-13
Ok, just re-installed ubuntu.
I will see if the method works, and then ill let you know.

One thing i have found, when i switch to the 'Back-End' of Linux, i can see this message

```
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
```

---

### Post by adam93250 on 2007-05-13
Ok, the method worked.
The wireless is working and im typin the message from it right now.

Thanks Everyone!

---

