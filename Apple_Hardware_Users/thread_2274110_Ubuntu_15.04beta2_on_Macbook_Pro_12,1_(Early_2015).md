---
title: "Ubuntu 15.04beta2 on Macbook Pro 12,1 (Early 2015) - can't connect to 5GHz wireless"
date: 2015-04-17
forum: Apple Hardware Users
---

### Post by HXn on 2015-04-17
I ran the wireless info dump script from [this post]("http://askubuntu.com/a/425205/399103") - my output is [here]("http://paste.ubuntu.com/10841397/").

[PHP]Network controller [0280]: Broadcom Corporation BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)[/PHP]

I copied [brcmfmac43602-pcie.bin]("https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/") into /lib/firmware/brcm which enabled the wireless to pick up some SSIDs, but not all (pretty sure just 2.4GHz).

Any help would be appreciated. Thanks!

---

### Post by raywang2 on 2015-06-02
Same here, 

there is a bug track of it, but seems like no one works on it...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1448567](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1448567)

---

