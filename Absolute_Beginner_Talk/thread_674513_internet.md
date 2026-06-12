---
title: "internet"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-01-21
i have finally installed ubuntu 7.10 onto my computer
trying to connected it to the internet
wired it up with a ehernet lead
top right hand corner shows that it is pluged in
but no internet.

any help?

cheers
Peter

---

### Post by spiderbatdad on 2008-01-21
maybe right click on network monitor and select "enable networking" If that doesn't work. try the terminal...```
ifconfig
ifdown eth0
```

you might have to use the manual configuration gui, and try setting mode to roaming.

---

### Post by pedrom169 on 2008-01-21
i typed in ifdown eth0
and its saying its not configured

---

### Post by spiderbatdad on 2008-01-21
did you try clicking network monitor and selecting manual configuration...then set to roaming mode?

---

### Post by ugm6hr on 2008-01-21
Give us some details about your internet connection first.

Do you have a router?  Or a direct ADSL modem?

If using a router - is it set for DHCP or fixed ip address?

If using an ADSL modem, what model?

Also - post the output from these 2 commands (case is important):
```
ifconfig
lshw -C network
```

---

