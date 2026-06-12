---
title: "Wifi stops working inexplicably"
date: 2020-02-27
forum: Apple Hardware Users
---

### Post by bigcfk on 2020-02-27
Hi,  I'm installing Ubuntu 16.04 (yes) on a 2011 MacBook Pro and am having  trouble with the WiFi. It worked while I installed it, and it had no  problems after I rebooted it. But then I performed an update, and now no  networks are listed. When I run "nmcli device status" I get:

  ```
 device type state connection
 wlp2s0 wifi disconnected --
 enp3s0 ethernet unavailable --
 lo loopback unmanaged --  
```

"nmcli general status" says there is no connectivity. I've  set the REGDOMAIN to the correct country code. I've removed and  reinstalled the Broadcom drivers and that didn't work. I tried  installing 18.04 but it wouldn't boot after installing.

  Can I downgrade network-manager? (I've read in one thread that this  solved it, but I've read several solved threads that don't work for me  :()
  
Thanks for any help!

---

### Post by wildmanne39 on 2020-02-27
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by bigcfk on 2020-02-27
Thanks for the quick reply!

Here is the output: paste.ubuntu.com/p/4xRs43vpkG

I next followed the Broadcom steps, and purged then installed "bcmwl-kernel-source". But no change.

---

