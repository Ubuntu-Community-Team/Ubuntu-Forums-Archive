---
title: "Why I can't conenct to internet no matter using wired or wireless?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by learn on 2008-02-18
Hi all,
I'm using ubuntu 7.10 and I had faced the internet connection problem for quite some time. When I use the wireless connection, it shows the connection status is active and around 70%. But I still can't access to internet or use my update manager to update my packages. So, after that, I try the wired connection by plug in a network cable and it shows the connection status is active too. But I also can't really access to any webpage or do update stuffs...Does anyone can help on this? thanks in advance.

---

### Post by kesman on 2008-02-18
right-click the network manager icon and disable your wireless connection if you have plugged yourself into the wired one. Then disable networking, and then enable it to refresh the network settings for the wired network. Then try again connecting.

---

### Post by jan quark on 2008-02-18
please post the results of these terminal commands

```
iwconfig
```
```

ifconfig
```

```
sudo iwlist scan
```
```

cat /etc/network/interfaces
```

---

### Post by learn on 2008-02-18
hi kesman, thanks for offering help. But this doesn't work for me.

---

### Post by oilchangeguy on 2008-02-18
try turning off the modem and router for about a minute, and reboot the computer.

---

### Post by learn on 2008-02-18
> **jan quark said:**
> please post the results of these terminal commands

```
iwconfig
```
```

ifconfig
```

```
sudo iwlist scan
```
```

cat /etc/network/interfaces
```

hi jan quark, thanks for help.
i had attached the sceenshot for the terminal commands result.
iwconfig: iwconfig.PNG

ifconfig: if.PNG

iwlist scan: iwlist_scan.PNG

cat: cat.PNG

---

### Post by justleen on 2008-02-18
in addition to the above, can you post the output of ```
nestat -nr 
``` as well?
(reading though your screens, the network config seems OK, imho)

---

### Post by bumanie on 2008-02-18
The symptoms you are describing, sound like they could possibly be related to the ipv6 problem that many have had with gutsy. You can blacklist ipv6 and see if that makes a difference. There are two methods, both of which are reversible if they don't work.

1) > sudo gedit /etc/modprobe.d/blacklist
at the end of the list type
blacklist ipv6
save and reboot.

2) type about:config in the firefox address bar
In the filter type ipv6
Right click on the ipv6 and change false to true using the toggle option

If it is the ipv6 issue, either of these work. If it makes no difference you can change it back to how it is now.

---

