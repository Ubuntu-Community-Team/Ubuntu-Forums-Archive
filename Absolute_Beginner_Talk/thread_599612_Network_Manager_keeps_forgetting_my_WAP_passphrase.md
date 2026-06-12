---
title: "Network Manager keeps forgetting my WAP passphrase"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by neekz on 2007-11-01
Hello, 

 I am having a problem with my Network manager in Gutsy Gibbon keeps forgetting my WAP key after reboot. It works great but every time I boot up I have to open Network Manager and re-enter my pass phrase. 

 Ndiswrapped Broadcom chipset, My Essid is set to broadcast and it has no issue remembering it or locating it. I am getting faster speeds in ubuntu then windows, just wish I didn't have to re enter my WAP after every boot up.

---

### Post by ddrichardson on 2007-11-01
Ah -- try this, open a terminal and type:```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```Should work now when you reboot.

---

### Post by neekz on 2007-11-01
No that didn't work still have Network Manager not remembering my WAP.

---

### Post by ddrichardson on 2007-11-01
Is the bcm43xx kernel module loaded as well as ndiswrapper? If it is then blacklist it. If not perhaps worth filing a bug report? The bcm43xx chipsets are surprisingly hard work.

---

### Post by neekz on 2007-11-01
I am not certain how do I blacklist something??

---

### Post by ddrichardson on 2007-11-01
Edit /etc/modprobe.d/blacklist and add the modules to blacklist:```

blacklist bcm43xx
```

---

### Post by neekz on 2007-11-01
> **ddrichardson said:**
> Edit /etc/modprobe.d/blacklist and add the modules to blacklist:```

blacklist bcm43xx
```

```
#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx
```

 Thats what I saw when I opened Blacklist. :confused:

---

