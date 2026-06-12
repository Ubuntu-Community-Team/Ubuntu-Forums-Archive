---
title: "Broadcom wireless card Macbook 5,1"
date: 2010-11-07
forum: Apple Hardware Users
---

### Post by Jawnskeel on 2010-11-07
Aluminum Unibody macbook, the only aluminum macbook to date. It has a Broadcom chip in it and I installed the STA drivers. The first day it seemed to work fine. Then I noticed pages stopped loading. The max throughput I get is like 30KiB/s once in a while. Sometimes I see consistent speeds of 600B/S...this really sucks. Is there a fix or anything?

I was going to make the switch slowly to 10.10 full-time, but the wireless issue is bothering me. The keyboard brightness keys don't work natively, but there's a fix I saw but didn't have time to implement earlier. I like ubuntu but I don't like my wireless not working!

---

### Post by sevenflo on 2010-11-07
I have the same issue with the Macbook 5,1. Except with me, I wasn't even able to get the STA driver to install.

Would really appreciate a workaround for this.

Also, Jawnskeel, where did you see a fix for the brightness keys? Mine worked before I installed the driver for NVIDIA. I was told in another thread it has nothing to do with the NVIDIA driver, it was a bios issue. That was for my SONY FZ. Now, same problem.

---

### Post by Jawnskeel on 2010-11-07
> **sevenflo said:**
> I have the same issue with the Macbook 5,1. Except with me, I wasn't even able to get the STA driver to install.

Would really appreciate a workaround for this.

Also, Jawnskeel, where did you see a fix for the brightness keys? Mine worked before I installed the driver for NVIDIA. I was told in another thread it has nothing to do with the NVIDIA driver, it was a bios issue. That was for my SONY FZ. Now, same problem.

[https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

I found that from a thread somewhere here after searching. I followed the instructions for the keyboard section, and it worked perfectly. After doing all the steps, I can easily turn the brightness up or down using the original F5 and F6 keys.

But this wireless issue is slightly different now. I'm now at home using my home connection, and it's not bad. I installed 126MB worth of updates with no issues and no slow speeds. I was actually maxing my downstream. However, it still sometimes takes like >10 seconds to get the data to start moving in and out properly. I don't know what it is, but where I was testing before with the result of 600B/s, it was a DSL modem connected to a linksys wr54t or whatever that base model is. Using an Belkin at home and it's noticeably better, but that 10 second lag for data starts moving is a bother.

On another note, I really enjoy linux. Not restarting into OSX any time soon :)  If the touchpad had all of the functionality it has in OSX, I think i'd expand my ubuntu partition to the whole drive :)

---

### Post by alexmurray on 2010-11-07
When running on battery the broadcom driver puts the wifi card into power saving mode which makes it start acting erratically and hence drops packets etc and becomes unreliable - so if this happens on battery you can type the following in a terminal window to disable power saving mode:

```
sudo iwconfig eth1 power off
```

---

