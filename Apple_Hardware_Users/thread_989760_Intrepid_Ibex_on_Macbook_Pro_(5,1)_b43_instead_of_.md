---
title: "Intrepid Ibex on Macbook Pro (5,1) b43 instead of wl?"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by mxweas on 2008-11-21
Intrepid Ibex already has support for the broadcom wl driver, but it does not support what I need. Has anyone had success with the b43 driver? I've tried installing b43-fwcutter with apt-get then using modprobe to start it and then blacklisting wl. The problem is when I start gdm, it doesn't even recognize a wireless adapter, is there something I need to do to start b43?

Thanks,
Max

---

### Post by cyberdork33 on 2008-11-23
it doesn't support the card in your Macbook pro yet.

---

### Post by mxweas on 2008-11-23
Is there anything besides b43 and wl, that will support my wifi card then?

Thanks,
Max

---

### Post by cyberdork33 on 2008-11-24
you can try ndiswrapper, but you need a windows driver that will support your card.

---

