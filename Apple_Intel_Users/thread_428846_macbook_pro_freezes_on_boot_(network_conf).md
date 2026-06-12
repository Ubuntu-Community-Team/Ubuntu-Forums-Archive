---
title: "macbook pro freezes on boot (network conf)"
date: 2007-04-30
forum: Apple Intel Users
---

### Post by teymour on 2007-04-30
I have a feisty installed on my macbook pro. I had problem with the networking configuration on boot : my computer froze while configuring the network. On grub quiet mode, I had the message  "BUG: soft lockup detected on CPU".

To solve it, I had modified the following files 

[LIST]
[*]/etc/modules
```

[...]
eth0
```
[*]/etc/iftab
```
[...]
eth1 mac <mac address> arp 1
```
[*]/etc/modprobe.d/ndiswrapper
```
[...]
alias eth1  ndiswrapper
```
[/LIST]

If you have the resolvconf package installed, you should remove if you do not want to experience empty resolv.conf file after boot.

---

### Post by Romu on 2007-05-01
Same issue for me. NDISWRAPPER doesn't work with Feisty on the Macbook Pro Core 2 Duo :
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/83224")

You can try to install Madwifi driver 0.9.30.10, it installs, the Atheros chipset set is well recognized and works...until you reboot...and...your Macbook Pro doesn't want to book anymore.

So welcome on the beautiful world of a buggy Feisty !! No more wireless.

---

### Post by ronocdh on 2007-05-01
Teymour, which chipset are you using? Give us the specific model (I believe Romu is using AR5008). Use **lspci** (after **sudo update-pciids**, if necessary) to do get the info.

---

