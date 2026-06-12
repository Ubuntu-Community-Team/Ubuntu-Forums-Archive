---
title: "Wireless works for a few hours then drops out"
date: 2007-10-15
forum: Apple Intel Users
---

### Post by wootwoot123 on 2007-10-15
I am running the 64 bit version of gutsy and am using the madwifi driver for my wireless. At random times the wireless will stop working. I am still connected and still have an ip address but I am not able to ping anything, even the default gateway. I am unsure of the problem or how to fix it so I reboot and everything goes back to normal. I can usually go for hours before this happens but there is no set frequency for it. Does anyone know how to fix this? Thank  you.

---

### Post by Namtabmai on 2007-10-15
There's a known problem with the madwifi as detailed here

[http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

Are you getting 
```

kernel: wifi0: rx FIFO overrun; resetting

```

In you kernel messages?

---

### Post by wootwoot123 on 2007-10-21
> **Namtabmai said:**
> There's a known problem with the madwifi as detailed here

[http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

Are you getting 
```

kernel: wifi0: rx FIFO overrun; resetting

```

In you kernel messages?

Has this been fixed or is wireless still flakey?

---

### Post by Stu09 on 2008-01-18
I just came across this thread after being frustrated at having to reboot everytime my wireless dropped out.
I read in that link, that if you suspend and wake up the computer again, your wifi works again. I just tested it out and my wireless is back on.

---

### Post by onyxrev on 2008-01-20
I have this problem too on my Macbook... 

The supposed temporary solution:

iwpriv ath0 bgscan 0

...does nothing.

It's really not good.

---

