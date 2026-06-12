---
title: "how to really turn off the wireless?"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by tchorix on 2007-07-02
Hi guys,

This question was probably asked before, but I couldn't find the answer any where... trying to get more battery life, I decided to stop the networking by doing

```

sudo /etc/init.d/networking stop

```

But that didn't really turned off the wireless, because it carries on with the roaming mode. Unfortunately, there's no way to stop the roaming mode from the networking configuration tool (or probably I didn't find it)... 

So I also tried

```

sudo iwconfig ath0 power off

```

but that didn't work either... any idea?

thanks a lot
cheers
Tchorix

---

### Post by benanzo on 2007-07-02
unload the wireless module:
```
sudo rmmod ath_pci
```

---

### Post by tchorix on 2007-07-02
That was it! thanks a lot

Tch

---

