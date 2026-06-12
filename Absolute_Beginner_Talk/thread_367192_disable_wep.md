---
title: "disable wep?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-02-21
hi,

our public library offers free wireless.  their setup is here:

QUICK SETUP GUIDE
1. Configure your laptop/ notebook or PDA as follows:
a. Network Type – Infrastructure Mode
b. SSID – PPL
c. Disable WEP and/or WPA
d. Enable DHCP
or
set IP address to autoconnect.


i understand everything except for c.  is wep on my wireless card?  i thought it was on the router.

i disable wep with:  iwconfig eth1 enc off.  no problem.  BUT iwconfig eth1 enc on gives me an error message reading:  SET failed on device eth1; Invalid argument.

what am i doing wrong?  how do i turn it back on?

thanks,
rich

---

### Post by n8bounds on 2007-02-21
security protocols are set by the access point, you are correct

just apt-get install gnome-network-manager, comment out everything of your /etc/networking/interfaces file that doesn't have to do with the loopback (lo) interface (then reboot) and you can gui your way thru all this...when joining the network (who's SSID is "PPL" apparently), just answer the encryption question with OPEN.

---

### Post by carlosfocker on 2007-02-21
you should just need to type

```
sudo iwconfig wlan0 essid ppl
sudo ifdown
sudo ifup
```

Wlan0 is the wireless interface name that might be called something else. Should be listed when you type 
```

iwconfig
```

---

### Post by richieboy on 2007-02-21
thanks for the help.  but i would like to cli this stuff.  can you tell me how to do it that way, please?  i really dig the cli and want to learn all i can that way.

thanks,

rich

---

### Post by carlosfocker on 2007-02-21
I'm guessing cli is command line interface, if so, see above post.  This will set the ssid with out using encryption.

---

### Post by richieboy on 2007-02-21
i get it!!  thanks.

---

