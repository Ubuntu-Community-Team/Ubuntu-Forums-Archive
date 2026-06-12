---
title: "Lost Sound Configuration"
date: 2008-01-06
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2008-01-06
Hi all.

Would someone mind doing me a quick favor? If you use a MacBook Santa Rosa, could you post the contents of this file:

```
sudo gedit /etc/modprobe.d/options
```

I deleted the contents for some reason trying to get Gutsy to interface with my sound card, but now I need it back.

Thanks in advance :)

---

### Post by RelativelyQuantum on 2008-01-07
'Cmon people; it's not that hard!

---

### Post by jeepxj97 on 2008-01-13
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

---

### Post by RelativelyQuantum on 2008-01-23
THANK YOU! Sorry about the belated post. Though I'm glad someone took the time to reply.

---

