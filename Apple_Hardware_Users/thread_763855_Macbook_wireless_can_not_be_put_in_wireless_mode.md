---
title: "Macbook wireless can not be put in wireless mode"
date: 2008-04-23
forum: Apple Hardware Users
---

### Post by ii bk ll on 2008-04-23
Hi,
I am trying to put my macbook into monitor mode and I always get this error

root@chris-laptop:/home/chris# iwconfig ath1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath1 ; No such device.
root@chris-laptop:/home/chris# iwconfig wifi0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wifi0 ; Operation not supported.

I am pretty new to linux and i hope that some one can help me with this issue. I am not sure if macbooks can not be put into monitoring mode or if there is something I need to do with getting the correct dirvers.

Thanks for any help,
Chris

---

### Post by benanzo on 2008-04-24
First verify that your wireless device is in fact ath1 (and not ath0 like it usually is.)

You need to use **wlanconfig** to change interface modes for Atheros chips like the one in the MacBooks.

```

$ sudo apt-get install madwifi-tools

```

To create a 'virtual' interface in monitor mode do:
```

$ sudo wlanconfig ath create wlandev wifi0 wlanmode monitor

```
That will return the name of the 'virtual' device it created, likely ath1 or ath2.
Now you can put it into monitor mode by doing:
```

$ sudo iwconfig ath1 mode monitor

```

To delete the 'virtual' interface do:
```

$ sudo wlanconfig ath1 destroy

```

Good Luck!

---

### Post by ii bk ll on 2008-04-24
Ok so I had madwifi installed and had the wifi working and then tried to do run the second code that you gave me and now my wireless does not work at all!!! I opened up my network tool and my wireless option is completely gone, its like my computer lost my wireless card!! Any help?

---

### Post by ii bk ll on 2008-04-24
I have tried to reinstall the madwifi drivers but nothing seems to work!!!

---

### Post by benanzo on 2008-04-24
```

$ sudo modprobe -r ath_pci
$ sudo modprobe ath_pci

```

That will reload the driver -- you don't need to reinstall.

I should have told you that creating a virtual device in monitor mode will eliminate the regular device in station mode.  You can create two devices though.  Might I ask why you need to manually put the device in monitor mode?  Most wifi sniffing tools (ie wireshark, kismet) will do it for you automatically.

Here's how to create two devices, one in station mode (for connecting to access points and browsing the internet) and one in monitor mode (for passively listening to traffic on the network):

```

$ sudo modprobe -r ath_pci
$ sudo modprobe ath_pci autocreate=none

  # This will return the name of the device in station mode (ath0)
$ sudo wlanconfig ath create wlandev wifi0 wlanmode sta

  # This will return the name of the device in monitor mode (ath1)
$ sudo wlanconfig ath create wlandev wifi0 wlanmode monitor

```

Now if you run:
```

$ iwconfig

```
You should see two devices, **ath0** in "Managed" mode (different term but means the same as "station" mode for wlanconfig) and **ath1** in "Monitor" mode.

NetworkManager will automatically re-connect to your wireless network using ath0, while ath1 will remain idle.

To undo everything you just did and go back to normal wireless operation do:
```

$ sudo modprobe -r ath_pci
$ sudo modprobe ath_pci

```

That simply reloads the driver.  This is not Windows, we don't have to reinstall our drivers every 10 mins.

Good Luck!

---

### Post by ii bk ll on 2008-04-24
Wireless works now!!! but when I enter the code 

sudo wlanconfig ath create wlandev wifi0 wlanmode sta

I get the error-

wlanconfig: ioctl: Input/output error

---

