---
title: "Ubuntu 11.10 - Slow and hot"
date: 2011-12-01
forum: Apple Hardware Users
---

### Post by nshiell on 2011-12-01
I'm running Ubuntu 11.10 on a MacBook 2,1 and the performance is low and the fan comes on and the laptop heats up allot.

Any settings I can change to get more appropriate performance?

---

### Post by deonis on 2011-12-01
You can always install last LTS 10.04 :) or if you want to play, today is arriving the new Alpha version of next LTS 12.04.

---

### Post by nshiell on 2011-12-01
Meh 10.04 had bad dual screen support and no Unity.
Maybe I will play with the LTS if I can get an ISO
Do you know if 12.04 will look at support as a priority?

---

### Post by BC59 on 2011-12-01
You can install Jupiter and manipulate the fan control and the temperature issues from it.

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

---

### Post by bluexrider on 2011-12-01
> **nshiell said:**
> I'm running Ubuntu 11.10 on a MacBook 2,1 and the performance is low and the fan comes on and the laptop heats up allot.

Any settings I can change to get more appropriate performance?

I think I would drop back to the 11.04 version. Seems as though it was running well on laptops.

---

### Post by mdgill on 2012-01-26
I have submitted a bug report about this overheating problem - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921714](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921714)

If you are having the same problem, please add to the bug report.

FYI, I had the same problem under 11.04.  10.04 LTS was no option because of the network management, sound problems, etc, etc, etc.  Installing the 3.2.1 upstream kernel helped some of my modem problems, but my system still crashes and is uncomfortably hot (I can barely rest my hands on the keyboard) even under low CPU usage.

---

### Post by nshiell on 2012-01-26
mdgill Thanks for escalating this to be a bug, I have started commenting on the bug report you made.

---

