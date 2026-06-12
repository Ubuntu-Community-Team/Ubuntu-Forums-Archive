---
title: "No built in ethernet found with X/K/Ubuntu on PB Lombard"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by nuke on 2006-06-06
Hello all!

I am unable to get any of X/K/Ubuntu - Desktop 6.06 to find my built in ethernet connection on my PB G3/Lombard.  I have used the live-cd and installed K&Xubuntu on the hard drive hoping one might work.

I can't find any record of the ethernet card using ifconfig.

Is there a way to get the live-disk or installed version to find the built in ethernet card?

(The built in ethernet was automatically found when using v5.10 live-cd!)

Thanks in advance.

---

### Post by ssam on 2006-06-07
does
```
ifconfig -a
```
not show it?

try
```
lspci
```

---

### Post by nkbj on 2006-06-07
This is a known problem. The BMAC ethernet driver is not loaded automatically by the dapper desktop CD installer. The alternate CD installer works.

To fix this you should add these lines to /etc/modules:
```

genrtc
bmac

```
The genrtc module is necessary to make the network connection work if your hardware clock is not set to UTC.

Regards,
Niels Kristian

---

### Post by nuke on 2006-06-07
Thank you ... My next question was going to be about getting the hardware clock to work.  Now I don't have to ask that anymore.

Thank you for the suggestions, I'll try it right away.

---

