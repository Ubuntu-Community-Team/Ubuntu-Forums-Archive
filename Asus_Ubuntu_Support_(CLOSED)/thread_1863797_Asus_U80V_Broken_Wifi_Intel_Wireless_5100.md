---
title: "Asus U80V Broken Wifi Intel Wireless 5100"
date: 2011-10-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mfinger on 2011-10-18
Has taken the better part of two days to fix, but I managed to fix a broken wireless wifi situation introduced in Ubuntu 11.10.

Using an Asus U80V I was able to connect to wireless networks, only for the connection to stop working after 5-10 seconds. Wired networking was fine.

The fix was adding 

```
options iwlagn 11n_disable=1
```to the file

```
/etc/modprobe.d/iwlagn.conf
```This file did not already exist and had to be created.

I did previously update the kernel to 3.06, without any change, so I am doubtful of any impact.

Hope that this helps anyone in the same situation as the Intel card (5100) seems to be having a lot of issues with recent Ubuntu versions.

---

### Post by ernestj on 2011-10-19
I have an ASUS U56. Do you think this will work for me? 

If so, please give detailed instructions. I am a new to this.

I do not know where to input the commands that you mentioned. 

In terminal?

Thanks,
ernie

---

