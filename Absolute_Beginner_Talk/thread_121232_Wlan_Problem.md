---
title: "Wlan Problem"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by kafitz22 on 2006-01-24
I apologize in advance if this is a stupid question, but then again, that's why I'm posting in this section.

I have a Netgear WG311 v2 Texas Instuments ACX111 wireless card. It works just fine, but when I don't use the internet for a little while, the connection drops and I can seem to reconnect without rebooting my computer. Is there anything I can do from terminal or any program I can get from Synaptic so I can reconnect?

Thanks.

---

### Post by carlosqueso on 2006-01-24
try doing ```
sudo ifdown wlan0
sudo ifup wlan0
``` or whatever the name of your wireless connection is to reconnect.  However that is an interesting problem and you might want to post over in the hardware->networking forum so hopefully somebody more knowledgeble than I can help you get it not to drop out at all.

---

### Post by kafitz22 on 2006-01-24
Thanks for the help. I'll see what they say.

---

