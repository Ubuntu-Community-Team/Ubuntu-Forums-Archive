---
title: "cant find window driver wireless card"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Tlingit on 2007-11-05
Hello,
i have looked everywhere can some one point me in the right direction to find my wireless card windows driver for the ndis wrapper?? please?


lspci

00:14:0 bridge nvidia corporation MCP51 Ethernet controller (rev a3)

lspci -n

00:14:0 0680: 10de:0269 (rev a3)

lspci -v

bridge: nvidia corporation MCP51 ethernet controller (rev a3)
subsystem: hewlett packard company unknown device 2a54
flags: bus master, 66mhz, fast devsel, latency 0, IRQ 16
memory at fe02bb000 (32_bit non prefetchable) [size=4k]
1/o perts at cc00 [size=8]
capibilities <access denied>

---

### Post by overdrank on 2007-11-05
> **Tlingit said:**
> Hello,
i have looked everywhere can some one point me in the right direction to find my wireless card windows driver for the ndis wrapper?? please?


lspci

[COLOR="Red"]00:14:0 bridge nvidia corporation MCP51 Ethernet controller (rev a3)[/COLOR]

lspci -n

00:14:0 0680: 10de:0269 (rev a3)

lspci -v

bridge: nvidia corporation MCP51 ethernet controller (rev a3)
subsystem: hewlett packard company unknown device 2a54
flags: bus master, 66mhz, fast devsel, latency 0, IRQ 16
memory at fe02bb000 (32_bit non prefetchable) [size=4k]
1/o perts at cc00 [size=8]
capibilities <access denied>

Hi and correct me if I am wrong but that is not a wireless adapter?

---

### Post by Maestro23 on 2007-11-05
I've got the same one in my Gateway Tower.  It is not wireless.  Had no problems connecting to the Internet.

> 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d400 [size=8]
        Capabilities: <access denied>


---

### Post by Tlingit on 2007-11-05
ok thank you that is what i was sorta thinking do you think you could possibly go to my other post and point it out for me. or could you please tel me how to find my wireless card

[http://ubuntuforums.org/showthread.php?t=603319](http://ubuntuforums.org/showthread.php?t=603319)

---

### Post by Tlingit on 2007-11-05
I am trying to get wireless through WPA this is my lanlords connection or i would have changed it. 

iwconfig

lo   no wireless
 
eth0 no wireless

wmaster ieee 802.11g  frequency:2.412 ghz
rts thr:off fragment thr 2346 b
              

wnlan0 ieee 802.11g  ESSID
mode manage frequency:1:412 ghz access point: not associated
RTS thr : off fragment thr =2346 b
link quality 0 signal level:0 noise level 0
rx invalid nwid:0 rx invalid crypt:0 rx invalid frag:
Tx excessive retries:0 invalid misc:0 missed beacon:

---

