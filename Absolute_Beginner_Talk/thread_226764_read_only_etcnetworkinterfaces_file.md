---
title: "read only /etc/network/interfaces file"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by rlynch on 2006-07-31
So I just installed Ubuntu 6.04(i believe), and am having issues connecting to my wireless.

A - it reads it as eth1 instead of wlan0. but i hear this isn't the end of the world, just a name/title for it. Which is ok with me.

B - here is my iwconfig for eth1(i hear this helps)
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


So it recognizes my card. But when I 'activate' it, it dosnt stay activated. If I close the System/Admin/Networking window, and open it back up. It's deactivated again. Also when I open the connection properties for it, it says 0% signal strength.

So I look around, and they say my /etc/network/interfaces file should read

```

auto eth1
iface eth1 inet dhcp
#wireless-essid linksys

```

Yet when I open the file, edit it, it doesn't allow me to save it. Says I only have read access. I right click it, go properties, and it says the owner is root. Yet my username is rlynch, It never asked me for a password for the root account.

Any thoughts? Thanks in advanced for any assistance.

---

### Post by christhemonkey on 2006-07-31
When you go to open it, you need to do so from a terminal like this:
```
gksudo gedit /etc/network/interfaces

```
This will allow you to edit it.

---

### Post by rlynch on 2006-07-31
i see, i dunno why there's no root account

thanks, that was able to allow me to edit it. but i see it doesn't help.

when i activate it, close it, and open it back up, it says it's still inactive. any idea why?



EDIT - you can close this. I found exactly what I was looking for

Thanks again!

---

### Post by christhemonkey on 2006-08-01
Could you please post a link to elighten others who find this thread with the same problem?

---

