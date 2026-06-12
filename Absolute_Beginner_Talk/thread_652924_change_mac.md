---
title: "change mac"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by prabesh708 on 2007-12-29
how can i change the mac address of the nic

---

### Post by Atreus12 on 2007-12-29
Simple
```

ifconfig [interface name] hw ether [new MAC address]

```

---

### Post by scorp123 on 2007-12-29
> **prabesh708 said:**
> how can i change the mac address of the nic ```
sudo apt-get install macchanger
``` ... then execute **macchanger --help** and it will show you the options. ```
GNU MAC Changer
Usage: macchanger [options] device

  -h,  --help                   Print this help
  -V,  --version                Print version and exit
  -s,  --show                   Print the MAC address and exit
  -e,  --endding                Don't change the vendor bytes
  -a,  --another                Set random vendor MAC of the same kind
  -A                            Set random vendor MAC of any kind
  -r,  --random                 Set fully random MAC
  -l,  --list[=keyword]         Print known vendors
  -m,  --mac=XX:XX:XX:XX:XX:XX  Set the MAC XX:XX:XX:XX:XX:XX 
```

---

